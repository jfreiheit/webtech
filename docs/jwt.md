# JSON Web Tokens (JWT)

Mithilfe von [JSON Web Tokens (JWT)](https://jwt.io/introduction) verwalten wir den Zugriff auf Webseiten. Wir werden JWTs hier ganz einfach dafür verwenden, um zu unterscheiden, ob eine Nutzerin bereits eingeloggt ist oder nicht. Zunächst nochmal zur Wiederholung: HTTP ist ein *zustandsloses* Protokoll. Das bedeutet insbesondere, dass der Webserver vorherige Anfragen desselben Clients nirgendwo speichert und somit auch nicht kennt. 

Prinzipiell ist es also gar nicht möglich, sich zunächst mit einer Anfrage beim Webserver einzuloggen und sich bei den folgenden Anfragen dann darauf zu beziehen. Eine Abhilfe dafür wird dadurch erreicht, dass der Webserver bei "Einloggen" ein *sicheres Token* generiert und dem Nutzer dieses Token übermittelt. Danach schickt der Nutzer dieses Token bei jeder Anfrage an den Webserver (im Header der Anfrage) mit. Der Webserver kann mithilfe dieses Tokens die Nutzerin identifizieren und eine eigene Historie über die Zugriffe anlegen, z.B. in einer Datenbank. Erst dadurch wird es möglich, dass man z.B. einen virtuellen Einkaufskorb befüllt.  

Ein JSON Web Token besteht aus drei Teilen:

- einem *Header*, der den Typ des Tokens enthält (`JWT`) und den Verschlüsselungsalgorithmus, der zur Verschlüsselung der Informationen verwendet wird, z.B. [`SHA256`](https://de.wikipedia.org/wiki/SHA-2).  
- einem *Paload*, der die Informationen über die Ntzerin enthält und eventuell weitere Informationen, wie z.B. Rolle der Nutzerin, z.B. `admin`
- einer *Signatur*, die mithilfe des angegebenen Verschlüsselungsalgorithmus die Inforationen des Headers und der Payload verschlüsselt. Mithilfe der Signatur kann überprüft werden, ob ide Informationen im Header oder im Payload geändert wurden oder nicht. 

Die drei Teile werden jeweils durch einen Punkt getrennt, d.h. ein JWT hat die Form `header.payload.signature`. 

Mithilfe des [Codierers/De-Codierers](https://jwt.io/#debugger-io) von JWT können Sie das Codieren bzw. Decodieren nachvollziehen. Angenommen, Ihr *Header* ist 

```jason
{
  "alg": "HS256",
  "typ": "JWT"
}
```

, d.h. Sie verwenden `SHA256` zur Verschlüsselung und der Typ ist `JWT`. Dann ist der erste Teil des JWT

```json
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9
```

Angenommen, Ihr *Payload* ist 

```jason
{
  "data": [
    {
      "id": 1,
      "username": "test",
      "email": "test@test.de",
      "password": "098f6bcd4621d373cade4e832627b4f6"
    }
  ],
  "iat": 1609061622
}
``` 

Die `data` haben die gleiche Struktur, wie wir sie später auch verwenden werden. Das Passwort `test` ist `md5`-verschlüsselt. `iat` steht für *issued at*  und gibt die Zeit ([Unix-Time](https://www.unixtimestamp.com/index.php)) an, zu der das JWT erzeugt wurde (hier 27.12.2020). Dann ist der zweite Teil des JWT

```json
eyJkYXRhIjpbeyJpZCI6MSwidXNlcm5hbWUiOiJ0ZXN0IiwiZW1haWwiOiJ0ZXN0QHRlc3QuZGUiLCJwYXNzd29yZCI6IjA5OGY2YmNkNDYyMWQzNzNjYWRlNGU4MzI2MjdiNGY2In1dLCJpYXQiOjE2MDkwNjE2MjJ9
```

Wenn Sie als "sichere" Passpharse `secret` wählen und damit die *Signatur* erstellen, dann ist der dritet Teil des JWT

```json
XBWOvX8OceGmx8u77YfsyQtupYYO9p9mUurvIqqwgdk
```

Sie werden diesen JWT (andere Zeit) später in Ihrer Anwendung wiederfinden. Ausführliche Informationen über JWT finden Sie [hier](https://jwt.io).

Wir werden JWT hier in der einfachsten Form anwenden:

- wir können uns registrieren und einloggen
- das Backend erzeugt beim Registrieren ein JWT und schickt es an den Client
- im Client speichern wir das JWT ab und verwenden es dann beim Zugriff auf die Webseite


## Login-Backend

Wir erstellen ein Backend mit dem folgenden Endpunkten: 

| Methode | URL | Bedeutung |
|---------|-----|-----------|
| `POST`    | `/user/register` | Registrierung - fügt einen neuen Datensatz hinzu |
| `POST`    | `/user/login` | Login - prüft, ob ein Nutzer in der Datenbank enthalten ist |

Für das Registrieren wird ein JSON in der folgenden Form (Beispieldaten) an das Backend gesendet:

```json
{
    "username": "test",
    "email": "test@test.de",
    "password": "test"
}
```

Für das Login wird die E-Mail-Adresse weggelassen und nur `username` und `password` übermittelt:

```json
{
    "username": "test",
    "password": "test"
}
```

Existiert der Nutzer `test` mit dem Passwort `test` in der Datenbank, so wird das folgende JSON vom Backend zum Frontend zurückgesendet:

```json
{
    "status": 1,
    "data": [
        {
            "id": 1,
            "username": "test",
            "email": "test@test.de",
            "password": "098f6bcd4621d373cade4e832627b4f6"
        }
    ],
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJkYXRhIjpbeyJpZCI6MSwidXNlcm5hbWUiOiJ0ZXN0IiwiZW1haWwiOiJ0ZXN0QHRlc3QuZGUiLCJwYXNzd29yZCI6IjA5OGY2YmNkNDYyMWQzNzNjYWRlNGU4MzI2MjdiNGY2In1dLCJpYXQiOjE2MDkwODIyMTF9.ou22aTCkagg_0hchSdO_dV5AHUDizPqp287dAUOpues"
}
```

Das Passwort wird nicht als Klarname in der Datenbank abgelegt, sondern verschlüsselt (als *Hash*) durch das [`md5`-Modul](https://www.npmjs.com/package/md5).

### `login`-Datenbank

Unter `localhost/phpmyadmin` (oder auf dem `studi.f4`-Server) eine Datenbank erstellen (z.B. `login`). Darin eine Tabelle `users` anlegen:

=== "SQL-Query zum Erstellen der Tabelle `users`"
	```sql
	--
	-- Tabellenstruktur für Tabelle `users`
	--

	CREATE TABLE `users` (
	  `id` int(11) NOT NULL AUTO_INCREMENT,
	  `username` varchar(255) NOT NULL,
	  `email` varchar(255) NOT NULL,
	  `password` varchar(255) NOT NULL
	) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

	--
	-- Indizes für die Tabelle `users`
	--

	ALTER TABLE `users`
	  ADD PRIMARY KEY (`id`);
	```

### Backend erzeugen

Wir erzeugen uns ein Backend namens `loginbackend`: 

```bash
mkdir loginbackend 
cd loginbackend 
npm init 
```

Nun installieren wir gleich alle `node`-Module, die wir im Backend benötigen:

```bash
npm install express --save
npm install nodemon
npm install cors
npm install mysql
npm install jsonwebtoken
npm install md5
```

Als erstes erstellen wir eine neue Datei `app.js` und geben ein:

=== "app.js"
	```js linenums="1"
	const express = require('express');
	const index_router = require('./controller/index');
	const cors = require('cors');
	const app = express();
	app.use(cors())
	app.use(express.json());
	app.use('/', index_router);
	app.listen(4000, () => {
	    console.log('listening on port 4000');
	})
	```

In Zeile `2` wird eine `controller/index.js` verwendet. Erzeugen Sie einen Ordner `controller` und darin eine `index.js`:

=== "controller/index.js"
	```js linenums="1"
	const express = require('express');
	const router = express.Router();
	const user = require('../model/user');
	router.use('/user', user);
	module.exports = router;
	```

In Zeile `3` wird eine `model/user.js` verwendet. Erzeugen Sie einen Ordner `model` und darin eine `user.js`:

=== "model/user.js"
	```js linenums="1"
	const express = require('express');
	const router = express.Router();
	const md5 = require('md5');
	const jwt = require('jsonwebtoken');
	const mysql = require('mysql');
	const con = mysql.createConnection({
	    host: "localhost",
	    user: "root",
	    password: "IhrPasswort",
	    database: "login"
	});
	router.post('/register', async function (req, res, next) {
	    try {
	        let { username, email, password } = req.body;
	        const hashed_password = md5(password.toString())
	        const checkUsername = `Select username FROM users WHERE username = ?`;
	        con.query(checkUsername, [username], (err, result, fields) => {
	            if(!result.length){
	                const sql = `Insert Into users (username, email, password) VALUES ( ?, ?, ? )`
	                con.query(
	                    sql, [username, email, hashed_password],
	                    (err, result, fields) =>{
	                        if(err){
	                            res.send({ status: 0, data: err });
	                        }else{
	                            let token = jwt.sign({ data: result }, 'secret')
	                            res.send({ status: 1, data: result, token : token });
	                        }
	                    })
	            }
	        });
	    } catch (error) {
	        res.send({ status: 0, error: error });
	    }
	});

	router.post('/login', async function (req, res, next) {
	    try {
	        let { username, password } = req.body;
	        const hashed_password = md5(password.toString())
	        const sql = `SELECT * FROM users WHERE username = ? AND password = ?`
	        con.query(
	            sql, [username, hashed_password],
	            function(err, result, fields){
	                if(err){
	                    res.send({ status: 0, data: err });
	                }else{
	                    let token = jwt.sign({ data: result }, 'secret')
	                    res.send({ status: 1, data: result, token: token });
	                }
	            })
	    } catch (error) {
	        res.send({ status: 0, error: error });
	    }
	});
	module.exports = router;
	```

Diese Datei ist recht umfangreich. Wir schauen uns die Details gleich näher an. Zunächst passen wir noch die `package.json` an, um mithilfe von `nodemon` unsere Anwendung zu starten (unter `script`):

=== "package.json"
	```json linenums="1" hl_lines="8"
	{
	  "name": "loginbackend",
	  "version": "1.0.0",
	  "description": "",
	  "main": "index.js",
	  "scripts": {
	    "test": "echo \"Error: no test specified\" && exit 1",
	    "start": "nodemon app.js"
	  },
	  "author": "",
	  "license": "ISC",
	  "dependencies": {
	    "cors": "^2.8.5",
	    "express": "^4.17.1",
	    "jsonwebtoken": "^8.5.1",
	    "md5": "^2.3.0",
	    "mysql": "^2.18.1",
	    "nodemon": "^2.0.6"
	  }
	}
	```

Starten Sie die Anwendung mit 

```bash
npm start
```

oder, noch besser, konfigurieren Sie das Ausführungskommando in Ihrer IDE, so dass Sie die Anwendung über den entsprechenden Button starten können: ![start](./files/114_start.png).

Wir verwenden dieses Mal `nodemon` zum Start der Anwenung. Das hat den Vorteil, dass wir `node` nicht jedes Mal aufrufen müssen, um das Backend zu starten. `nodemon` ist noch nicht wirklich ausgetestet, funktioniert aber in den meisten Fällen schon recht gut, weshalb wir es hier ausprobieren. Es ist nur für die Entwicklung empfohlen. Das Backend sollte sich jetzt ausführen lassen. 

### Backend testen

Wir testen das Backend mithilfe von Postman. Starten Sie das Backend und öffnen Sie Postman. Geben Sie als `POST`-Anfrage `http://localhost:4000/user/register` ein und senden Sie im `body` (als `JSON`) die Daten

```json
{
    "username": "test",
    "email": "test@test.de",
    "password": "test"
}
```

mit: 

![postman](./files/115_postman.png)

Der User `test` wird mit den entsprechenden Informationen in der Datenbank abgelegt. Das Passwort ist dabei verschlüsselt. Die Response des Servers ist etwas in der Art: 

```json
{
    "status": 1,
    "data": {
        "fieldCount": 0,
        "affectedRows": 1,
        "insertId": 1,
        "serverStatus": 2,
        "warningCount": 0,
        "message": "",
        "protocol41": true,
        "changedRows": 0
    },
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJkYXRhIjpbeyJpZCI6MSwidXNlcm5hbWUiOiJ0ZXN0IiwiZW1haWwiOiJ0ZXN0QHRlc3QuZGUiLCJwYXNzd29yZCI6IjA5OGY2YmNkNDYyMWQzNzNjYWRlNGU4MzI2MjdiNGY2In1dLCJpYXQiOjE2MDkwNjE2MjJ9.XBWOvX8OceGmx8u77YfsyQtupYYO9p9mUurvIqqwgdk"
}
```

In der Datenbank sehen Sie den Eintrag:

![mysql](./files/117_mysql.png)

Nach dem Registrieren können Sie auch das EInloggen testen. Geben Sie als `POST`-Anfrage `http://localhost:4000/user/login` ein und senden Sie im `body` (als `JSON`) die Daten

```json
{
    "username": "test",
    "password": "test"
}
```

mit: 

![postman](./files/116_postman.png)

Die Response hat die folgende Form:

```json
{
    "status": 1,
    "data": [
        {
            "id": 1,
            "username": "test",
            "email": "test@test.de",
            "password": "098f6bcd4621d373cade4e832627b4f6"
        }
    ],
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJkYXRhIjpbeyJpZCI6MSwidXNlcm5hbWUiOiJ0ZXN0IiwiZW1haWwiOiJ0ZXN0QHRlc3QuZGUiLCJwYXNzd29yZCI6IjA5OGY2YmNkNDYyMWQzNzNjYWRlNGU4MzI2MjdiNGY2In1dLCJpYXQiOjE2MDkwNjE2MjJ9.XBWOvX8OceGmx8u77YfsyQtupYYO9p9mUurvIqqwgdk"
}
```

Das Backend erzwugt den JWT bei jedem Login neu. Es gibt also ein *Session-JWT*. Eine andere Möglichkeit wäre, das JWT beim Registrieren zu erzeugen und eebenfalls in der Datenbank abzuspeichern und es dann immer mitzuschicken. 

Wir schauen uns nun nochmal die `user.js` genauer an:

=== "model/user.js"
	```js linenums="1"
	const express = require('express');
	const router = express.Router();
	const md5 = require('md5');
	const jwt = require('jsonwebtoken');
	const mysql = require('mysql');
	const con = mysql.createConnection({
	    host: "localhost",
	    user: "root",
	    password: "IhrPasswort",
	    database: "login"
	});
	router.post('/register', async function (req, res, next) {
	    try {
	        let { username, email, password } = req.body;
	        const hashed_password = md5(password.toString())
	        const checkUsername = `Select username FROM users WHERE username = ?`;
	        con.query(checkUsername, [username], (err, result, fields) => {
	            if(!result.length){
	                const sql = `Insert Into users (username, email, password) VALUES ( ?, ?, ? )`
	                con.query(
	                    sql, [username, email, hashed_password],
	                    (err, result, fields) =>{
	                        if(err){
	                            res.send({ status: 0, data: err });
	                        }else{
	                            let token = jwt.sign({ data: result }, 'secret')
	                            res.send({ status: 1, data: result, token : token });
	                        }
	                    })
	            }
	        });
	    } catch (error) {
	        res.send({ status: 0, error: error });
	    }
	});

	router.post('/login', async function (req, res, next) {
	    try {
	        let { username, password } = req.body;
	        const hashed_password = md5(password.toString())
	        const sql = `SELECT * FROM users WHERE username = ? AND password = ?`
	        con.query(
	            sql, [username, hashed_password],
	            function(err, result, fields){
	                if(err){
	                    res.send({ status: 0, data: err });
	                }else{
	                    let token = jwt.sign({ data: result }, 'secret')
	                    res.send({ status: 1, data: result, token: token });
	                }
	            })
	    } catch (error) {
	        res.send({ status: 0, error: error });
	    }
	});
	module.exports = router;
	```

In den Zeilen `6-11` definieren wir den Zugang zur Datenbank. Achten Sie hier auf das richtige Passwort und den korrekten Namen der Datenbank. In den zeilen `12-35` wird die *Registrierungs*-Funktion definiert und in den zeilen `37-55` die *Login*-Funktion. 

In der Registrierungsfunktion wird zunächst überprüft, ob der `username` bereits in der Datenbank existiert (Zeilen `16-17`). Wenn nicht, wird der Nutzer in der Datenbank angelegt (Zeilen `19-20`) und das JWT wird erzeugt (Zeile `26`). Die Daten und das JWT werden vom Backend zusammen mit dem `status: 1` als Response zurückgeschickt, wenn alles fehlerlos geklappt hat. Beachten Sie, dass beim Erstellen des JWT als "sichere" Passphrase das Wort `secret` verwendet wird  (Zeile `26`). Das Pasowrt wird mittels `md5` gehasht - es wird also verschlüsselt abgelegt (Zeile `15`). 

Die Login-Funktion ist der Registrierungs-Funktion sehr ähnlich. Es wird der passende `username` in der Datenbank gesucht und das gehashte Passowrt verglichen. Auch hier wird ein JWT erzeugt. 


## Login-Frontend

Für das Frontend erstellen wir uns ein Formular zur Registrierung und ein Formular für das Login. Das JWT, das wir vom Webserver erhalten, speichern wir lokal ab. Dazu verwenden wir `localStorage`. Wir nennen unser Frontend `loginfrontend`:

```bash
ng new loginfrontend 
```

Wir erzeugen uns zwei Komponenten, eine für die Registrierung und die andere für das Login:

```bash
cd loginfrontend 
ng g c login 
ng g c register 
```

Wir binden beide Komponenten über Routing ein. In der `app-routing.module.ts` definieren wir dazu:

=== "app-module.routing.ts"
	```javascript linenums="1" hl_lines="7-8"
	import { NgModule } from '@angular/core';
	import { Routes, RouterModule } from '@angular/router';
	import {LoginComponent} from './login/login.component';
	import {RegisterComponent} from './register/register.component';

	const routes: Routes = [
	  {path: 'login', component: LoginComponent},
	  {path: 'register', component: RegisterComponent},
	];

	@NgModule({
	  imports: [RouterModule.forRoot(routes)],
	  exports: [RouterModule]
	})
	export class AppRoutingModule { }
	```

Damit die Formulare schicker aussehen, binden wir Bootstrap ein:

```bash
npm install --save bootstrap
npm install --save jquery
npm install --save popper.js
```

In der `angular.json` Bootstrap hinzufügen:

=== "angular.json (Auszug)"
	```json linenums="1" hl_lines="6 10-11"
    "assets": [
      "src/favicon.ico",
      "src/assets"
    ],
    "styles": [
      "./node_modules/bootstrap/dist/css/bootstrap.css",
      "src/styles.css"
    ],
    "scripts": [
      "./node_modules/jquery/dist/jquery.js",
      "./node_modules/bootstrap/dist/js/bootstrap.js"
    ]
	```

Die Zeilen müssen zwei Mal eingefügt werden. Einmal unter `"build"` und einmal unter `"test"`. Achten Sie darauf, zunächst `jQuery` einzubinden und erst dann `bootstrap.js`. 

### Services im Frontend

Wir erstellen uns zwei Services. Der eine Service `api` ist für die Kommunikation mit dem Backend zuständig. Der andere Service `auth` legt den Token im `localStorage` ab und holt ihn auch von dort. 

```bash
ng g service services/auth
ng g service services/api 
```

In der `services/api.service.ts`:

=== "services/api.service.ts"
	```js linenums="1"
	import { Injectable } from '@angular/core';
	import { environment } from '../../environments/environment';
	import { HttpClient } from '@angular/common/http';
	import { map } from 'rxjs/operators';
	@Injectable({
	  providedIn: 'root'
	})
	export class ApiService {
	  baseUrl = 'http://localhost:4000/';
	  constructor(private http: HttpClient) {}

	  postTypeRequest(url, payload): any {
	    return this.http.post(`${this.baseUrl}${url}`, payload).pipe(map(res => {
	      return res;
	    }));
	  }
	}
	```


In der `services/auth.service.ts`:

=== "services/auth.service.ts"
	```js linenums="1"
	import { Injectable } from '@angular/core';
	@Injectable({
	  providedIn: 'root'
	})
	export class AuthService {
	  constructor() { }

	  getUserDetails(): any {
	    return localStorage.getItem('userData') ? JSON.parse(localStorage.getItem('userData')) : null;
	  }

	  setDataInLocalStorage(variableName, data): any {
	    localStorage.setItem(variableName, data);
	  }

	  clearStorage(): any {
	    localStorage.clear();
	  }
	}
	```

Mit der `getUserDetails()`-Funktion laden wir die `userData` aus dem `localStorage`, mit der `setDataInLocalStorage()`-Funktion speichern wir die `userData` im `localStorage` und `clearStorage()` löscht den gesamten `localStorage`. 

### Registrierungs-Komponente

In der Registrierungskomponente erstellen wir das Formular zur Registrierung und rufen mit den eingebgebenen Daten das Backend zur Registrierung auf. 

In der `register.component.ts`: 

=== "src/app/register/register.component.ts"
	```javascript linenums="1"
	import { Component, OnInit } from '@angular/core';
	import { ApiService } from './../services/api.service';
	import { AuthService } from './../services/auth.service';
	import {FormBuilder, FormGroup, Validators} from '@angular/forms';
	import { Router } from '@angular/router';

	@Component({
	  selector: 'app-register',
	  templateUrl: './register.component.html',
	  styleUrls: ['./register.component.css']
	})
	export class RegisterComponent implements OnInit {
	  isLogin = false;
	  errorMessage;
	  registerForm: FormGroup;
	  submitted = false;

	  constructor(
	    private formBuilder: FormBuilder,
	    private api: ApiService,
	    private auth: AuthService,
	    private router: Router
	  ) { }

	  // convenience getter for easy access to form fields
	  get f(): any { return this.registerForm.controls; }

	  ngOnInit(): void {
	    this.registerForm = this.formBuilder.group({
	      username: ['', Validators.required],
	      email: ['', Validators.required],
	      password: ['', Validators.required]
	    });
	    this.isUserLogin();
	  }

	  onSubmit(): void {
	    this.submitted = true;
	    console.log('Your form data : ', this.registerForm.value);
	    this.api.postTypeRequest('user/register', this.registerForm.value).subscribe((res: any) => {
	      if (res.status) {
	        console.log(res);
	        this.auth.setDataInLocalStorage('userData', JSON.stringify(res.data));
	        this.auth.setDataInLocalStorage('token', res.token);
	        this.router.navigate(['login']);
	      } else {
	        console.log(res);
	        alert(res.msg);
	      }
	    }, err => {
	      this.errorMessage = err.error.message;
	    });
	  }

	  isUserLogin(): void{
	    if (this.auth.getUserDetails() != null){
	      this.isLogin = true;
	    }
	  }
	}
	```

Im Konstruktor (Zeilen `18-23`) werden die beiden Services, der `FormBuilder` und das `Router`-Modul per dependency injection eingebunden. In der `ngOnInit()`-Funktion (Zeilen `28-35`) definieren wir das Formular bestehend aus den `FormControls` `username`, `email` und `password`. Das gesamte Formular ist in der Eigenschaft `registerForm` gespeichert (Zeile `15`). Für den Zugriff auf die einzelnen `FormControls` defineiren wir noch einen Getter `f()`, der uns Schreibarbeit in der `register.component.html` erspart (`f()` gibt uns ein Objekt der drei `FormControls` des Formulars zurück). 

Die Funktion `onSubmit()` wird aufgerufen, wenn das Formular abgeschickt wird. In Zeile `39` geben wir die Daten des Formulars auf die Konsole aus (nur für Debug-Zwecke). In den Zeilen `40-52` rufen wir die Funktion `postTypeRequest` aus unserem `api`-Service auf. Darin übergeben wir alle Daten aus dem Formular. Wenn alles klappt (`status` der Response ist `1`), dann speichern wir alle Daten lokal unter `userData` (Zeile `43`) und das JWT nochmal extra unter `token` (Zeile `44`). Danach rufen wir die Route `login` auf, wechseln also zur Login-Komponente. 

Das Template der Registrierungs-Komponente sieht wie folgt aus:

=== "src/app/register/register.component.html"
	```html linenums="1"
	<div class = 'row m-0 w-100'>
	  <div class = 'col-md-4 offset-4 mt-5' *ngIf = '!this.isLogin'>
	    <h4>Register</h4>
	    <form [formGroup]="registerForm" (ngSubmit)="onSubmit()" >
	      <div class = 'form-group'>
	        <input class = 'form-control' type = "text" formControlName="username" name = "username" placeholder = "Username" [ngClass]="{ 'is-invalid': submitted && f.username.errors }" />
	        <div *ngIf="submitted && f.username.errors" class="invalid-feedback">
	          <div *ngIf="f.username.errors.required">Username is required</div>
	        </div>
	      </div>
	      <div class = 'form-group'>
	        <input class = 'form-control' type = "email" formControlName="email" name = "email" placeholder = "Email" [ngClass]="{ 'is-invalid': submitted && f.email.errors }" />
	        <div *ngIf="submitted && f.email.errors" class="invalid-feedback">
	          <div *ngIf="f.email.errors.required">E-Mail is required</div>
	        </div>
	      </div>
	      <div class = 'form-group'>
	        <input class = 'form-control' type = "password" formControlName="password" name = "password" placeholder = "Password" [ngClass]="{ 'is-invalid': submitted && f.password.errors }" />
	        <div *ngIf="submitted && f.password.errors" class="invalid-feedback">
	          <div *ngIf="f.password.errors.required">Password is required</div>
	        </div>
	      </div>
	      <input class= 'btn btn-outline-info' type = "submit" value = "Register">
	    </form>
	  </div>
	  <div class = 'col-md-4 offset-4 mt-5' *ngIf = 'this.isLogin'>
	    <h5>You are logged in</h5>
	  </div>
	</div>
	```

Die Direktive `*ngIf = '!this.isLogin'` in Zeile `2` prüft den Status der Eigenschaft `isLogin`. Diese ist am Angang `false` (siehe `register.component.ts` in Zeile `13`). Durch die `isUserLogin()`-Funktion der `register.component.ts` (Zeilen `55-59`) kann der Wert auf `true` gesetzt werden, wenn der `auth`-Service `userData` gespeichert hat. Für den Fall. dass `isLogin` den Wert `true` hat, zeigt die Registrierungs-Komponente `You are logged in` an (Zeilen `26-28`). Wenn nicht, erscheint das Registrierungsformular (Zeilen `2-25`). Beim Absenden des Formulars wird die `onSubmit()`-Funktion aus `register.component.ts` aufgerufen. Für die einzelnen Eingabefelder wird ein Atrributbinding definiert: Falls das Formular abgeschickt wurde (`submitted`) und aber Fehler existieren (z.B. `f.username.errors`), wird dem entsprechenden Eingabefeld die Bootstrap-Klasse `is-invalid` zugeordnet und es erscheint die darunter definierte Fehlerausgabe. Hier findet auch die `f()`-Funktion ihre Anwendung. 


### Login-Komponente 

Die Login-Komponente hat starke Ähnlichkeit mit der Registrierungs-Komponente. Das Formular enthält jedoch keinen Eintrag für die E-Mail und es wird eine ander URL im Backend aufgerufen `user/login` anstelle von `user/rgister`. Außerdem stellt die Login-Komponente noch einen Button `Log-out` zur Verfügung, der ein Ausloggen ermöglicht (`logout()`-Funktion). Das Ausloggen wird hier dadurch simuliert, dass der `localStorage` gelöscht wird. Ansonsten sehen sich swohl die `ts`- als auch die `html`-Datei sehr ähnlich: 

=== "src/app/login/login.component.ts"
	```javascript linenums="1"
	import { Component, OnInit } from '@angular/core';
	import {FormBuilder, FormGroup, Validators} from '@angular/forms';
	import { ApiService } from './../services/api.service';
	import { AuthService } from './../services/auth.service';
	import { Router } from '@angular/router';
	@Component({
	  selector: 'app-login',
	  templateUrl: './login.component.html',
	  styleUrls: ['./login.component.css']
	})
	export class LoginComponent implements OnInit {
	  isLogin = false;
	  errorMessage;
	  loginForm: FormGroup;
	  submitted = false;

	  constructor(
	    private formBuilder: FormBuilder,
	    private api: ApiService,
	    private auth: AuthService,
	    private router: Router
	  ) { }

	  ngOnInit(): void {
	    this.loginForm = this.formBuilder.group({
	      username: ['', Validators.required],
	      password: ['', Validators.required]
	    });
	    this.isUserLogin();
	  }

	  // convenience getter for easy access to form fields
	  get f(): any { return this.loginForm.controls; }

	  onSubmit(): void {
	    this.submitted = true;
	    console.log('Your form data : ', this.loginForm.value);
	    this.api.postTypeRequest('user/login', this.loginForm.value).subscribe((res: any) => {
	      if (res.status) {
	        console.log(res);
	        this.auth.setDataInLocalStorage('userData', JSON.stringify(res.data));
	        this.auth.setDataInLocalStorage('token', res.token);
	        this.router.navigate(['']);
	      } else {
	      }
	    }, err => {
	      this.errorMessage = err.error.message;
	    });
	  }

	  isUserLogin(): void{
	    console.log(this.auth.getUserDetails());
	    if (this.auth.getUserDetails() != null){
	      this.isLogin = true;
	    }
	  }

	  logout(): void{
	    this.auth.clearStorage();
	    this.router.navigate(['']);
	  }
	}
	```

=== "src/app/login/login.component.html"
	```html linenums="1"
	<div class = 'row m-0 w-100'>
	  <div class = 'col-md-4 offset-4 mt-5' *ngIf = '!this.isLogin'>
	    <h4>Login</h4>
	    <form [formGroup]="loginForm" (ngSubmit)="onSubmit()" >
	      <div class = 'form-group'>
	        <input class = 'form-control' type = "text" formControlName="username" name = "username" placeholder = "Username" [ngClass]="{ 'is-invalid': submitted && f.username.errors }" />
	        <div *ngIf="submitted && f.username.errors" class="invalid-feedback">
	          <div *ngIf="f.username.errors.required">Username is required</div>
	        </div>
	      </div>
	      <div class = 'form-group'>
	        <input class = 'form-control' type = "password" formControlName="password" name = "password" placeholder = "Password" [ngClass]="{ 'is-invalid': submitted && f.password.errors }" />
	        <div *ngIf="submitted && f.password.errors" class="invalid-feedback">
	          <div *ngIf="f.password.errors.required">Password is required</div>
	        </div>
	      </div>
	      <input class= 'btn btn-outline-info' type = "submit" value = "Login">
	    </form>
	  </div>
	  <div class = 'col-md-4 offset-4 mt-5' *ngIf = 'this.isLogin'>
	    <h1>You are logged in</h1>
	    <button class = 'btn btn-outline-info' (click) = 'logout()'>Log-out</button>
	  </div>
	</div>
	```

Die `app.component.html` können Sie sich gestalten, wie Sie möchten. Eine Möglichkeit wäre so:

=== "app.component.html"
	```html linenums="1"
	<nav class="navbar navbar-expand-lg navbar-light bg-light">
	  <a class="navbar-brand" [routerLink] = "['/']" routerLinkActive = "active">Home</a>
	  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
	    <span class="navbar-toggler-icon"></span>
	  </button>
	  <div class="collapse navbar-collapse" id="navbarNav">
	    <ul class="navbar-nav">
	      <li class="nav-item">
	        <a class="nav-link" [routerLink] = "['login']" routerLinkActive = "active">Login</a>
	      </li>
	      <li class="nav-item">
	        <a class="nav-link" [routerLink] = "['register']" routerLinkActive = "active" >Register</a>
	      </li>
	    </ul>
	  </div>
	</nav>
	<router-outlet></router-outlet>
	```

Die entsprechenden Seiten sehen dann so aus:

![jwt](./files/121_login.png)

## Ausblick

Beachten Sie, dass das Beispiel bewusst einfach gehalten wurde. Es fehlen mehrere Sachen:

- wir reagieren im Frontend gar nicht auf Fehler des Backends, d.h. es fehlen z.B.
	- Reaktionen beim Registrieren, falls der `username` bereits existiert,
	- Reaktionen beim Login, falls das Passwort nicht korrekt ist
- wir haben keine Zugriffssteuerung definiert, d.h. es fehlt noch eine Seite (Komponente), auf die nur dann zugegriffen werden kann, wenn der Nutzer eingeloggt ist

Die Fehlerpunkte wären sicherlich eine gute Übung für Sie. Den letzten Punkt betrachten wir beim nächsten Mal. Allerdings kann man JWT auch noch so erweitern, dass bestimmte Rollen hinterlegt und abgefraget werden können. Das werden wir uns nicht anschauen. Aber vielleicht haben Sie ja bereits selbst Ideen, wie das geschehen kann. Die Nutzerdaten müssten ja nur im ein Attribut `role` erweitert und abgefragt werden. Umfassende Informationen darüber finden Sie im [JWT-Handbuch](./files/jwt-handbook-v0_14_1.pdf).

### Dowmloads der aktuellen Versionen

Clonen von Github:

- [loginfrontend](https://github.com/jfreiheit/loginfrontend)
- [loginbackend](https://github.com/jfreiheit/loginbackend)

im Folgenden wird auf diesen Versionen aufgebaut. 

## Zugriff nur bei Login

UserService

```bash
ng g s services/user
```

UserComponent

```bash
ng g c user
```

[Bearer Authentication](https://swagger.io/docs/specification/authentication/bearer-authentication/)
