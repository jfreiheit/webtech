# Node.js

## Installation

Installationsanweisungen für Ihr Betriebssystem finden Sie auf der Node.js-Webseite [https://nodejs.org/](https://nodejs.org). Nach der Installation können Sie überprüfen, ob node erfolgreich installiert wurde. Geben Sie dazu im Terminal

```
node -v
```

ein. Es sollte die Versionsnummer erscheinen, z.B. `v13.3.0`.

Da es sich bei JavaScript um eine Skriptsprache handelt, kann jede Anweisung durch den Interpreter interpretiert und ausgeführt werden. Deshalb lässt sich Node.js auch als im interaktiven Modus auf der Kommandozeile testen. Geben Sie dazu im Terminal 

```
node 
```

ein. Es erscheint etwas in der Art

```
Welcome to Node.js v13.3.0.
Type ".help" for more information.
> 
```

Node.js befindet sich dann im *Read-Eval-Print-Loop (REPL)*. Die im Terminal eingegebenen Kommandos werden gelesen (*read*), evaluiert (*eval*), ausgegeben (*print*) und auf das nächste Kommando gewartet (*loop*). Geben Sie im Terminal 

```
console.log("Hello FIW!");
```

ein. Es erscheint

```
Hello FIW!
undefined
```

Sie verlassen REPL durch Eingabe von `.exit`.

!!! success
    Somit ist Node.js installiert.

## Der erste eigene Webserver

Wir verwenden Node.js, um einen Webserver zu implementieren. Insbesondere wird dieser Webserver Anfragen (*requests*) unserer Webanwendung (des Clients) empfangen und verarbeiten. Die Verarbeitung wird meistens ein Zugriff auf eine Datenbank sein. Als Antwort (*response*) wird der Webserver die angefragten Daten an unsere Anwendung zurücksenden. 

Wir werden nun unseren ersten einfachen Webserver mithilfe von Node.js implementieren. Erstellen Sie sich in Ihrem `workspace` ein Verzeichnis `backend` und darin eine Datei `server.js` (das kann natürlich alles auch anders heißen). Öffnen Sie die Datei mit Ihrer IDE und geben Sie folgendes ein:

=== "server.js"
    ```javascript linenums="1"
	const http = require('http');

	const server = http.createServer(function(request,response) {
		response.writeHead(200, { 'content-type': 'text/plain; charset=utf-8'});
		response.write('Hello ');
		response.end('FIW!\n');
	});

	server.listen(8080, function() {
		console.log('Server is listening to http://localhost:8080');
	});
    ``` 

Wechseln Sie im Terminal in Ihr `backend`-Verzeichnis. Darin befindet sich die `server.js`. Geben Sie ein:

```bash
node server.js
```

Sie erhalten die Ausgabe `Server is listening to http://localhost:8080`. 

!!! fail "Port bereits belegt"
	Sollten Sie den Fehler `Error: listen EADDRINUSE:::8080` erhalten, so ist der Port `8080` bei Ihnen bereits durch eine andere Anwendung belegt. Dann wählen Sie einen anderen Port, z.B. `8081`. 


!!! success
    Ihr Webserver läuft nun!

Dies können wir auf verschiedene Arten testen:

1. Geben Sie `http://localhost:8080` in Ihren Browser ein. Es erscheint `Hello FIW!` im Browser. 
2. Nutzen Sie [`curl`](../tools/#curl) und geben Sie im Terminal `curl http://localhost:8080` ein. Es erscheint `Hello FIW!` im Terminal. 
3. Nutzen Sie ['Postman'](../tools/#postman) und geben Sie in das Eingabefeld neben `GET` die URL `http://localhost:8080` ein und klicken auf `Send`. Es erscheint `Hello FIW!` im unteren Teil des Fensters (Reiter `Body`).

Der Webserver läuft nun so lange, bis wir ihn beenden. Wir betrachten das obige Listing im Detail. In Zeilennummer 1 wird das [`http`-Modul von Node.js](https://nodejs.org/api/http.html) geladen und der Variablen `http` zugewiesen. Das Laden von Modulen erfolgt in Node.js mithilfe der Funktion `require()`. In Zeilennummer 3 wird ein Webserver mithilfe des `http`-Moduls erzeugt (`createServer()`). Das `http`-Modul bietet auch die Möglichkeit, einen Client zu erzeugen - aber das machen wir nicht mit Node.js sondern mit Angular. In Zeile 9 geben wir an, dass der Webserver nun permanent am Port `8080` auf Anfragen *lauschen* soll. Als 2. Parameter der `listen()`-Funktion hätte auch ein `HOST` angegeben werden können, also die IP-Adresse des Webservers. Wird keine IP-Adresse angegeben, so wie hier, ist es in unserem Fall `localhost`. Dann folgt eine [*Callback*-Funktion](../javascript/#callback-funktionen), die einen String auf die Konsole ausgibt, sobald die Verbindung steht. In den Zeilen 4 bis 6 ist die Antwort (*response*) des Webservers auf eine Anfrage (*request*) des Clients definiert. Die Funktion, die diese Antwort erstellt, ist eine Callback-Funktion der `createServer`-Funktion (in Zeile 3). Diese Callback-Funktion besitzt die beiden Parameter `request` und `response`. In diesem ersten Beispiel wird nur eine Response definiert. Diese besteht aus einem *HTTP-Header* (`writeHead()`) und einem *HTTP-Body* (`write()` + `end()`). Die Funktion `writeHead()`, die den HTTP-Header erzeugt, besitzt 2 Parameter. Der erste Parameter ist der [HTTP-Status-Code](https://developer.mozilla.org/de/docs/Web/HTTP/Status). Der Status-Code `200` besagt, dass die Anfrage (*request*) vom Server empfangen wurde und die Antwort (*response*) in dieser Nachricht enthalten ist. Der eigentliche HTTP-Header wird mit dem zweiten Parameter übertragen. In diesem Fall übermittelt der Server dem Client die Informationen, dass es sich bei der Antwort um reinen Text handelt (`content-type:text-plain`) und dass der HTTP-Body unter Verwendung des Zeichensatzes [UTF-8](https://www.ionos.de/digitalguide/websites/webseiten-erstellen/utf-8-codierung-globaler-digitaler-kommunikation/) (`charset=utf-8`) kodiert ist. Der HTTP-Body wird mit der `write()`-Funktion übertragen und mit der `end()`-Funktion abgeschlossen. In diesem Fall besteht der Body aus der Zeichenkette `Hello FIW!`. 

## Eine Erweiterung der Antwort

Im obigen Beispiel bestand die Antwort aus reinem Text. Wir erweitern die Antwort nun und senden vom Webserver an den Client als Body eine vollständige HTML-Seite.

=== "server.js"
    ```javascript linenums="1"
	const http = require('http');

	const server = http.createServer(function(request,response) {
		response.writeHead(200, { 'content-type': 'text/html; charset=utf-8'});

		const body = `<!DOCTYPE html>
		  <html>
		    <head>
		      <meta charset="utf-8">
		      <title>WebTech - Node.js</title>
		    </head>
		    <body>
		      <h1 style="color:#76B900">Hello FIW!</h1>
		    </body>
		  </html>`;

		response.end(body);
	});

	server.listen(8080, function() {
		console.log('Server is listening to http://localhost:8080');
	});
    ``` 

Achten Sie darauf, dass der `content-type` nun `text/html` ist, nicht mehr `text/plain` (Zeile 4). Sollte Ihr Server aus dem vorherigen Beispiel noch laufen, so müssen Sie ihn zunächst beenden. Geben Sie im Termina zum Beenden des Prozesses `node server.js` einfach `Strg+C` (`Ctrl+C`) und sarten Sie den Server unter Eingabe von

```bash
node server.js
```

erneut. Rufen Sie im Browser `http://localhost:8080/` auf. Es erscheint

![server.js](./files/28_node.png)

Sie können ja auch mal den `content-type` erneut auf `text/plain` setzen und den Server erneut starten (1. `Ctrl+C` und 2. `node server.js`), um zu sehen, welche Bedeutung die Angabe des `content-type` hat.

### Template-String

Im obigen Beispiel ist der String `body` in Backtick-Zeichen &#96; eingeschlossen. Das nennt man *Template-String* und ermöglicht mithilfe von `${}` Ausdrücke bzw. Variablen auszuwerten. Im Folgenden ist eine solche Verwendung einer Variable gezeigt. 

=== "Template-String"
    ```javascript linenums="1"
	const http = require('http');

	const server = http.createServer(function(request,response) {
		response.writeHead(200, { 'content-type': 'text/html; charset=utf-8'});

		const name = 'FIW!';
		const body = `<!DOCTYPE html>
		  <html>
		    <head>
		      <meta charset="utf-8">
		      <title>WebTech - Node.js</title>
		    </head>
		    <body>
		      <h1 style="color:#76B900">Hello ${ name }</h1>
		    </body>
		  </html>`;

		response.end(body);
	});

	server.listen(8080, function() {
		console.log('Server is listening to http://localhost:8080');
	});
    ```

In Zeile 6 wird eine Variable `name` definiert, der der String `FIW!` zugewiesen wird. In Zeile 14 wird mithilfe von `${ name }` der Wert der Variable `name` in das HTML eingebunden, so dass der Inhalt der Überschrift `<h1>` zu `Hello FIW!` ausgewertet wird.

### URLs auswerten

Eine URL kann um Schlüssel-Werte-Paare (*Parameter*) erweitert werden, um Daten mit der URL an den Webserver zu senden (siehe [**HTML --> URLs**](../html/#urls)). Ein Schlüssel-Werte-Paar wird immer durch ein `=` verbunden:

```bash
key=value
```

Das erste Schlüssel-Werte-Paar wird hinter ein `?` an die URL gehängt. Jedes weitere Paar wird mit einem `&` angebunden:

```bash
http://www.example.org/?key1=value1&key2=value2&key3=value3
```

Wir werden jetzt diese Parameter auswerten. Dazu laden wir einerseits ein weiteres Modul, nämlich das `url`-Modul und wir werten die Anfrage (*request*) dahingehend aus, dass wir die Parameter der URL auswerten. 

=== "server.js"
    ```javascript linenums="1"
	const http = require('http');
	const url  = require('url');

	const server = http.createServer(function(request,response) {
		response.writeHead(200, { 'content-type': 'text/html; charset=utf-8'});

		const parsedUrl = url.parse(request.url, true);
		const params = parsedUrl.query;

		const body = `<!DOCTYPE html>
			  <html>
		    <head>
		      <meta charset="utf-8">
		      <title>WebTech - Node.js</title>
		    </head>
		    <body>
		      <h1 style="color:#76B900">Hello ${ params.name } in ${ params.ort }</h1>
		    </body>
		  </html>`;

		response.end(body);
	});

	server.listen(8080, function() {
		console.log('Server is listening to http://localhost:8080');
	});
    ```

Nach dem restart des Webservers (1. `Ctrl+C` und 2. `node server.js`) und der Eingabe folgender URL: `http://localhost:8080/?name=FIW&ort=Berlin` wird im Browser Folgendes angezeigt:

![Node.js](./files/29_node.png)
