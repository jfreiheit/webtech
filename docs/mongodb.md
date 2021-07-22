# MongoDB und Node.js

[MongoDB] ist die am meisten verwendete *NoSQL (not only SQL)* Datenbank. Sie basiert nicht auf Relationen, Tabellen und ihren Beziehungen zueinander (ist also keine *relationale* Datenbank), sondern speichert Dokumente in JSON-ähnlichem Format. Die [Community Edition der MongoDB](https://github.com/mongodb/mongo) ist Open Source und kostenlos verfügbar. 
Sollten Sie mit *Visual Studio Code* arbeiten, sollten Sie sich am besten die [MongoDB for VS Code](https://code.visualstudio.com/docs/azure/mongodb)-Ereiterung installieren. 


```
mkdir MongoDBBackend
cd MongoDBBackend
npm init
```

- erstellt `package.json`

```
npm install express
npm install nodemon
```

- `nodemon` könnte auch (besser) als *Dev-Dependency* erstellt werden, aber ist okay hier

- `package.json` sieht jetzt so aus:

=== "package.json"
	```json linenums="1"
	{
	  "name": "mongodbbackend",
	  "version": "1.0.0",
	  "description": "",
	  "main": "index.js",
	  "scripts": {
	    "test": "echo \"Error: no test specified\" && exit 1"
	  },
	  "author": "J.Freiheit",
	  "license": "ISC",
	  "dependencies": {
	    "express": "^4.17.1",
	    "nodemon": "^2.0.9"
	  }
	}
	```

- wir werfen das `test`-Script raus und fügen dafür ein `start`-Skript ein, welches `nodemon` aufruft (und `app.js`, die wir uns gleich noch erstellen)


=== "package.json"
	```json linenums="1" hl_lines="7"
	{
	  "name": "mongodbbackend",
	  "version": "1.0.0",
	  "description": "",
	  "main": "index.js",
	  "scripts": {
	    "start": "nodemon app.js"
	  },
	  "author": "J.Freiheit",
	  "license": "ISC",
	  "dependencies": {
	    "express": "^4.17.1",
	    "nodemon": "^2.0.9"
	  }
	}
	```

- jetzt `app.js` im Projektverzeichnis erstellen und


=== "app.js"
	```js linenums="1"
	const express = require('express');

	const app = express();

	// Endpunkte (Funktionsaufrufe - Middleware)
	app.use('/test1', () => {
	    console.log('das könnte alles eine Funktion sein');
	})

	// Routen
	app.get('/', (req, res) => {
	    res.send('Hello FIW! (home)');
	});

	app.get('/test', (req, res) => {
	    res.send('Hello FIW! (home/test)');
	});


	app.listen(3000); // port 3000
	```

- im Terminal `npm run start` eingeben
- im Browser `localhost:3000` eingeben, es erscheint `Hello FIW! (home)`
- im Browser `localhost:3000/test` eingeben, es erscheint `Hello FIW! (home/test)`
- im Browser `localhost:3000/test1` eingeben, im Browser erscheint gar nichts (keine *Response*), aber im Terminal (dort, wo `npm run start` ausgeführt wurde) erscheint `das könnte alles eine Funktion sein`
- **übrigens**: hätten wir `app.use('/test', () => {` geschrieben, gäbe es nur die Ausgabe auf die Konsole, aber keine Ausgabe im Browser, da die *Middleware* nicht bis zur *Response* kommt (müsste man noch erstellen)

- zu *Routen mit Express* siehe [hier](https://expressjs.com/de/guide/routing.html)
- die  `app.use('/test', () => {` löschen wir wieder


=== "app.js"
	```js linenums="1"
	const express = require('express');

	const app = express();

	// Routen
	app.get('/', (req, res) => {
	    res.send('Hello FIW! (home)');
	});

	app.get('/test', (req, res) => {
	    res.send('Hello FIW! (home/test)');
	});


	app.listen(3000); // port 3000
	```

- wir installieren [Mongoose]

```bash
npm install mongoose
```

- Mongoose stellt eine einfach zu verwendende Schnittstelle zwischen Node.js und MongoDB bereit
- aber die MongoDB benötigen wir trotzdem (wir könnten auch eine Cloud von MongoDB oder z.B. mlab.com verwenden)

- bevor wir uns mit der MongoDB verbinden, erstellen wir zunächst noch eine Datenbank
- im Terminal geben wir `mongo` ein und dort

```bash
> use rest
```

(ohne das `>` - das oll nur symbolisieren, dass wir in der MongoDB-Shell sind). Es entsteht die Datenbank `rest`. Wir befüllen diese Datenbank probehalber mit Daten (löschen wir wieder)

```
> db.user.insert({name: "Ada Lovelace", age: 206})
```

- Falls Sie *Visual Studio Code*  verwenden und darin die [MongoDB for VS Code](https://code.visualstudio.com/docs/azure/mongodb)-Ereiterung installiert haben, können Sie auf der linken Seite auf das MongoDB-Blatt klicken und das `Advanced Connection Settings mit dem Formular `Open form` anklicken.

Sie geben `mongodb://127.0.0.1:27017` ein und dass Sie keine Authentifizierung verwenden. Öffnen Sie die `connection` und darin `rest` und es erscheint

```json
{
  "_id": {
    "$oid": "60ddc2e80de75bf12565e491"
  },
  "name": "Ada Lovelace",
  "age": 206
}
```

- Um sich in Node.js mit der DB zu verbinden, geben Sie 

=== "app.js"
	```js linenums="1" hl_lines="2 15-20"
	const express = require('express');
	const mongoose = require('mongoose');
	const app = express();

	// Routen
	app.get('/', (req, res) => {
	    res.send('Hello FIW! (home)');
	});

	app.get('/test', (req, res) => {
	    res.send('Hello FIW! (home/test)');
	});

	// connect to mongoDB
	mongoose.connect('mongodb://127.0.0.1:27017/rest', { useNewUrlParser: true, useUnifiedTopology: true });
	const db = mongoose.connection;
	db.on('error', console.error.bind(console, 'connection error:'));
	db.once('open', () => {
	    console.log('connected to DB');
	});

	app.listen(3000); // port 3000
	```

ein. Im Terminal sollte dann

```bash
[nodemon] restarting due to changes...
[nodemon] starting `node app.js`
connected to DB
```

erscheinen. 

- für die "geheimen" Zugangsdaten (die jetzt noch gar nicht "geheim" sind) verwenden wir das [dotenv](https://www.npmjs.com/package/dotenv)-Paket

```bash
npm install dotenv
```

- Im Projektordner erstellen wir und eine Datei `.env` (mit Punkt!) und schreiben darein:


=== ".env"
	```js linenums="1"
	DB_CONNECTION = 'mongodb://127.0.0.1:27017/rest';
	```

und in die `app.js`:


=== "app.js"
	```js linenums="1" hl_lines="4 16"
	const express = require('express');
	const mongoose = require('mongoose');
	const app = express();
	require('dotenv/config');

	// Routen
	app.get('/', (req, res) => {
	    res.send('Hello FIW! (home)');
	});

	app.get('/test', (req, res) => {
	    res.send('Hello FIW! (home/test)');
	});

	// connect to mongoDB
	mongoose.connect(process.env.DB_CONNECTION, { useNewUrlParser: true, useUnifiedTopology: true });
	const db = mongoose.connection;
	db.on('error', console.error.bind(console, 'connection error:'));
	db.once('open', () => {
	    console.log('connected to DB');
	});

	app.listen(3000); // port 3000
	```



