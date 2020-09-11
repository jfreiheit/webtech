# Type- und JavaScript

JavaScript wurde 1995 von Brendan Eich entwickelt. Er arbeitete damals bei Netscape und entwickelte mit dem damals sogenannten LiveScript eine Skriptsprache für den damaligen Netscape-Browser. Ein damaliger Browser "verstand" HTML und CSS. HTML sah für Nutzerinteraktionen nur das Klicken auf Hyperlinks vor. Andere Nutzerinteraktionen waren nicht vorgesehen. Mithilfe von JavaScript wurde eine Schnittstelle geschaffen, um durch Nutzerinteraktionen den HTML-Code zu manipulieren, ohne dass ein weiteres Nachladen vom Webserver notwendig wurde. Mit der Einführung von JavaScript wurden die Fähigkeiten von Browsern erweiteret, indem nun nicht mehr nur HTML und CSS interpriert wurde, sondern auch JavaScript - alles Client-seitig, also durch den Browser selbst. 

JavaScript ist eine sogenannte *Skriptsprache*, d.h. der Quellcode wird nicht compiliert und dann der übersetzte Byte- oder Maschinencode ausgeführt, sondern der Quellcode wird durch einen Interpreter interpretiert. Allerdings wird für Optimierungen JavaScript - insbesondere serverseitig in Node.js - durch sogenannte *Engines* doch in Maschinencode übersetzt, welcher ausgeführt wird. Die bekannteste dieser Engines ist die [Google-Engine V8](https://v8.dev/). Die Technologie der Compilierung wird als *Just-in-time-Kompilierung (JIT)* bezeichnet. 

JavaScript kennt (im Gegensatz zu TypeScript) keine Klassen. Das Objektmodell von JavaScript basiert auf *Prototypen*. Eigenschaften und Methoden können zur Laufzeit den Objekten hinzugefügt werden. Neben diesem *dynamischen* Objektmodell ist auch die Typisierung in JavaScript dynamisch. Der Typ einer Variable hängt vom Wert ab. Mit dem Wert kann sich auch der Typ der Variable ändern. 

## JavaScript

### `var`, `let` und `const`

Mithilfe der Schlüsselwörter `var`, `let` und `const` können in JavaScript Variablen deklariert werden. Wenn Sie eine Variable mit `var` deklarieren, dann ist diese Variable innerhalb der gesamten Funktion, in der Sie die Variable deklarieren, gültig. Dagegen hat `let` nur eine *Blockgültigkeit*, d.h. eine mit `let` deklarierte Variable ist nur in dem Anweisungsblock gültig, in dem sie deklariert wurde. Eine mit `let` deklarierte Variable verhält sich also wie eine in Java deklarierte Variable. `const` wird zur Deklaration von Konstanten verwendet. Es ist zu bachten: Falls es sich bei der mit `const` deklarierten Konstante um eine Referenzvariable handelt (also auf ein Objekt oder Array zeigt), dann kann diese Variable ihre Referenz zwar nicht mehr ändern, das jeweilige Objekt, auf das die Variable (konstant) zeigt, kann sich aber schon ändern.

### Arrow-Funktionen

*Arrow-Funktionen* werden auch als *Lambda-Ausdrücke* bezeichnet. Eine Arrow-Funktion ist eine Kurzschreibweise für eine anonyme Funktion. Anstelle von `function()` schreibt man nur noch einen  Pfeil. Enthält die anonyme Funktion sogar nur ein Argument (Parameter), kann man links vom Pfeil sogar die runden Klammern weglassen. Auch die geschweiften Klammern des Funktionskörpers können entfallen. Wenn die geschweiften Klammwern weggelassen werden, dann entspricht die rechte Seite des Pfeils dem Rückgabewert der Funktion, d.h. es kann sogar `return` weggelassen werden. Folgende Funktionsdefinitionen sind äquivalent:

```javascript
function(foo) = {return foo+1;}
(foo) => {return foo+1;}
foo => {return foo+1;}
foo => foo+1;
```

### Callback-Funktionen

Eine *Callback*-Funktion ist eine Funktion, die einer anderen Funktion als Parameter übergeben wird. Callback-Funktionen sind z.B. [hier](https://developer.mozilla.org/en-US/docs/Glossary/Callback_function) erläutert. Darin finden Sie auch das folgende einfache Beispiel einer Callback-Funktion:

``` javascript linenums="1"
function greeting(name) {
  alert('Hello ' + name);
}

function processUserInput(callback) {
  var name = prompt('Please enter your name.');
  callback(name);
}

processUserInput(greeting);
```

In den Zeilen 1-3 wird eine Funktion `greeting()` definiert, welche einen `name` erwartet. Diese Funktion gibt `Hello ` zusammen mit dem Namen in einem Alarmfenster aus. Die Funktion `greeting()` wird als *Callback*-Funktion in der Funktion `processUserInput()` (Zeilen 5-8) verwendet. Das heißt, die Funktion `greeting()` wird der Funktion `processUserInput()` als Parameter übergeben. Innerhalb der Funktion `processUserInput()` heißt die Referenz auf die Funktion `greeting()` `callback`. Der Parametername kann beliebig gewählt werden. Wir die Funktion `processUserInput()` aufgerufen (Zeile 10) und die Funktion `greeting()` als Parameter übergeben, dann erscheint zunächst ein Eingabefenster, in dem der Name eingeben wird und dieser Name wird der `greeting()`-Funktion als Parameter übergeben. Es erscheint das Alarmfenster mit der Ausgabe `Hello ` plus dem Namen. Der Funktion `processUserInput()` könnte auch jede andere Funktion als Callback-Funktion übergeben werden. 


## JSON 

JavaScript Object Notation 

## Promises

Eine *Promise* ist das Ergebnis einer asynchronen Operation. Es gibt vier Status einer Promis (uns interessiert in der Regel nur `resolved` oder `rejected`):

| *Status* | *Erklärung* |
|----------|-------------|
| `pending` | die Promise wartet noch auf die Beendigung der asynchronen Operation |
| `settled` | die asynchrone Operation wurde beendet |
| `resolved` | die asynchrone Operation wurde **erfolgreich beendet** |
| `rejected` | die asynchrone Operation **ist fehlgeschlagen** |

Um das Prinzip einer Promise zu erläutern, schauen wir uns ein Beispiel aus [**Node.js --> Eine Movie-Datenbank**](../node/#eine-movie-datenbank) an:

```javascript
function getAll() {
	return new Promise((resolve, reject) => {
		const query = 'SELECT * FROM Movies';
		connection.query(query, (error, results) => {
			if(error) reject(error);
			else	  resolve(results);
		})
	});
}
``` 

Die Funktion `getAll()` gibt eine Promise zurück. Diese wird mit dem Konstruktor erzeugt. Dem Konstruktor wird eine Callback-Funktion übergeben. Hier ist diese Funktion die Anfrage an die Datenbank `connection.query()`. Diese Funktion ist asynchron, d.h. sie wird ausgeführt, ohne dass andere Funktionsaufrufe stoppen müssen. Man kann auch sagen, dass die Promise die asynchrone Funktion *kapselt*. 

Die asynchrone Funktion enthält ebenfalls eine Callback-Funktion. Hier wurden als Parameternamen der Callback-Funktion `error` und `results` gewählt. Der erste Parameter wirft einen Fehler, wenn die asynchrone Funktion fehlschlägt, der zweite Parameter enthält die Daten bei Erfolg. Mit `reject` gibt man den Fehler zurück (im Fehlerfall) und mit `resolve` die Daten (im Erfolgsfall). 

!!! note "return new Promise()"
	Wir merken uns also: die `getAll()`-Funktion gibt ein `Promise`-Objekt zurück.

Wie kann eine solche Promise nun verwendet werden? Dazu schauen wir uns erneut das Beispiel aus [**Node.js --> Eine Movie-Datenbank**](../node/#eine-movie-datenbank) an:

```javascript
function listAction(request, response) {
    model.getAll().then(
        movies => response.send(view(movies)),
        error => response.send(error),
    );
}
```

Der entscheidende Punkt ist, dass ein Promise-Objekt eine `then`-Methode besitzt. Dieser `then`-Methode können wiederum zwei Callback-Funktionen übergeben werden. Die erste Funktion wird durch die `resolve`-Funktion der Promise aufgerufen, die zweite Funktion, falls die Promise die `reject`-Funktion aufruft. Werden der `resolve`- und der `reject`-Funktion Argumente übergeben (so wie oben `resolve(results)` und `reject(error)`), dann können diese Argumente in der jeweiligen Callback-Funktion ausgewertet werden (`results`-->`movies` bzw. `error`-->`error`). 

Die `then`-Funktion selbst gibt übrigens wieder ein `Promise`-Objekt zurück. Somit können mehrere Promises verkettet werden.

