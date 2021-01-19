# Web-Technologien

Herzlich willkommen zur WebTech-Veranstaltung! 

### Grober Inhalt

In dieser Veranstaltung lernen Sie, was das World Wide Web ist und wie man eigene Webseiten und -anwendungen realisiert. Sie lernen die Protokolle und Sprachen ``http``, ``HTML``, ``CSS``und ``JavaScript`` kennen und machen sich mit ``Angular``, ``Node.js`` und ``REST`` vertraut.  

Nachfolgend der vorläufige Wochenplan (wird eventuell angepasst). Die Vorlesungsvideos finden Sie darunter für die einzelnen Wochen (unter [**Inhalte**](http://freiheit.f4.htw-berlin.de/webtech/#inhalte)).

| | Woche | Themen (Vorlesung) | Übung | Aufgabe (Stand) | Abgabe Übung bis | 
|-|-------|--------------------|-------|-----------------|------------------|
| 1. | 05.-09.10.2020 | Einführung und Organisatorisches | Übung 0 | - | - | 
| 2. | 12.-16.10.2020 | HTML | Übung 1 | Idee | 25.10.2020 | 
| 3. | 19.-23.10.2020 | CSS (Eigenschaften und Selektoren) | Übung 2 | - | 01.11.2020 | 
| 4. | 26.-30.10.2020 | RWD (Responsive Webdesign) | Übung 3 | Konzept | 08.11.2020 | 
| 5. | 02.-06.11.2020 | JavaScript (DOM, Events, DOM-Funktionen) | Übung 4 | - | 15.11.2020 | 
| 6. | 09.-13.11.2020 | JavaScript (JSON, AJAX) | Übung 5 | Datenmodell | 22.11.2020 | 
| 7. | 16.-20.11.2020 | Angular (Einführung und Komponenten) | Übung 6 | Schnittstelle | 29.11.2020 | 
| 8. | 23.-27.11.2020 | Angular (Material und Routen) | Übung 7 | Frontend (c+r)| 13.12.2020 | 
| 9. | 30.-04.12.2020 | Node.js + Express (REST-Server + MySQL) | Übung 8 | Frontend (u+d)| 20.12.2020 | 
| 10. | 07.-11.12.2020 | Angular (Anbindung ans Backend I) | Übung 9 | Frontend fertig | 10.01.2020 | 
| 11. | 14.-18.12.2020 | Angular (Anbindung ans Backend II) | Übung 10 | Backend ( c ) | 17.01.2020 | 
| 12. | 21.-25.12.2020 | -  | - | Backend ( r ) | - |
| | | | | | | |
| 13. | 04.-08.01.2021 | JWT | - | Backend (u) | - |
| 14. | 11.-15.01.2021 | Drittanbieter-APIs  | - | Backend (d + fertig)| - |
| 15. | 18.-22.01.2021 | Wiederholung | - | fertig stellen | - |
| 16. | 25.-29.01.2021 | - | Fragen | Abgabe 1.PZ 13.02.2021 | - |
|  |  |  |  | Abgabe 2.PZ 01.04.2021 | - |

### Organisatorisches 

Zur erfolgreichen Durchführung der Veranstaltung müssen Sie die Übungen lösen und zu den jeweiligen Fristen per Git auf einen Server (GitHub oder GitLab) laden. Am Ende des Semesters ist eine Aufgabe abzugeben. Diese Aufgabe wird bewertet. Die Bewertung entspricht dann der Modulnote. 

Hier sind die Übungen beschrieben, die Sie in jeder Woche ausführen sollen. Damit Sie dies erfolgreich erledigen können, ist jeweils angegeben, welche Themen Sie dafür durcharbeiten müssen. Das Durcharbeiten der jeweiligen Themen entspricht jeweils einer Vorlesung. Diese wird also selbständig durchgeführt. 

Für die Kommunikation untereinander verwenden wir [**Slack**](https://slack.com/intl/de-de/). Dort können Sie alle inhaltlichen und organisatorischen Fragen stellen. Ich fände es gut, wenn ich dort möglichst wenig Fragen - zumindest die inhaltlichen - beantworten müsste, sondern eine Art internes Diskussionsforum entsteht. Es ist sehr gewünscht, dort Fragen zu stellen und noch mehr gewünscht, diese von Ihnen dort beantwortet zu sehen. Damit wäre allen geholfen und ich kann besser erkennen, wo noch Nachhol- bzw. Erläuterungsbedarf bei den meisten besteht.  

### Inhalte

??? question "Woche 1 - Einführung und Organisatorisches"
	- siehe **Übungsaufgabe 0**
	- <iframe src="https://mediathek.htw-berlin.de/media/embed?key=aa2dc92b4a4b18e89e85a195be581512&width=720&height=405&autoplay=false&autolightsoff=false&loop=false&chapters=false&related=false&responsive=false&t=0" data-src="" class="iframeLoaded" width="720" height="405" frameborder="0" allowfullscreen="allowfullscreen" allowtransparency="true" scrolling="no"></iframe>
	- die Notizen dazu finden Sie [**hier**](./files/01_WebTech_Einfuehrung.pdf)
	- <iframe src="https://mediathek.htw-berlin.de/media/embed?key=e4f7b04a1f1065daf8ecaeff5e99fd62&width=720&height=540&autoplay=false&autolightsoff=false&loop=false&chapters=false&related=false&responsive=false&t=0" data-src="" class="iframeLoaded" width="720" height="540" frameborder="0" allowfullscreen="allowfullscreen" allowtransparency="true" scrolling="no"></iframe>
	- die Notizen dazu finden Sie [**hier**](./files/02_Organisatorisches.pdf)

??? question "Woche 2 - Hypertext Markup Language (HTML)"
	- siehe [**HTML**](./html/#html)
	- siehe **Übungsaufgabe 1 (HTML)**
	- <iframe src="https://mediathek.htw-berlin.de/media/embed?key=6d5f322f330f0a9a46cd6d6b5486a51f&width=720&height=450&autoplay=false&autolightsoff=false&loop=false&chapters=false&related=false&responsive=false&t=0" data-src="" class="iframeLoaded" width="720" height="450" frameborder="0" allowfullscreen="allowfullscreen" allowtransparency="true" scrolling="no"></iframe>
	- hier die Bilder [**htw.jpg**](./files/htw.jpg) und [**fiw.jpg**](./files/fiw.jpg)

??? "index.html aus HTML-Vorlesung"
	```html
	<!DOCTYPE html>
	<html lang="de">
	<head>
	    <meta charset="UTF-8">
	    <title>HTML-Einführung</title>
	</head>
	<body>
	    <h1>große Überschrift</h1>
	    neuer Text
	    <p>ein erster Absatz</p>
	    <h3>kleinere Überschrift</h3>
	    <p> noch ein Absatz</p>

	    Vorteile von HTML:
	    <ul>
	        <li>Syntax und Semantic frei definierbar   </li>
	        <li>von Menschen lesbar</li>
	        <li>in Programmiersprachen einbettbar</li>
	        <li>offen für zukünftige Entwicklungen</li>
	    </ul>

	<!-- das ist ein Kommentar -->
	<p>das ist ein längerer Absatz <br/>
	das ist Text auf der nächsten Zeile </p>

	    <img src="./images/fiw.jpg" alt="FIW-Logo" style="width: 200px;" title="Mouseover-Effekt Informatione, die erscheinen, wenn wir mit der Maus drüber fahren"/>

	<h3>Input-Elemente</h3>

	<input type="text" />
	<input type="radio" />
	<input type="checkbox" checked="checked" />
	<input type="datetime-local" />

	<h3>Hyperlinks</h3>

	das ist Text <a href="http://www.htw-berlin.de" target="_blank">
	    <img src="./images/htw.jpg" alt="HTW Logo" />
	</a> das ist weiterer Text
	    <p>
	        <a href="./Unter/dok1.html">Dok 1</a>
	    </p>

	<h3>Container</h3>

	<section>
	    <header>ein Absatz</header>
	    <article>noch ein Absatz</article>
	    <footer>noch ein Absatz</footer>
	</section>
	<div>
	    <p>ein Absatz</p>
	    <p>noch ein Absatz</p>
	    <p>noch ein Absatz</p>
	</div>

	<h3>Formulare</h3>

	<form method="post">
	    <input type="text" name="user" placeholder="user"/>
	    <input type="password" name="pwd"/>
	    <button type="submit">Login</button>
	</form>

	<ul>
	    <li><a href="http://freiheit.f4.htw-berlin.de/webtech/html/#http-anfragemethoden" target="_blank">HTTP-Anfragemethoden</a> </li>
	    <li><a href="http://freiheit.f4.htw-berlin.de/webtech/html/#http-statusmeldungen" target="_blank">HTTP-Statusmeldungen</a> </li>
	    <li><a href="http://freiheit.f4.htw-berlin.de/webtech/html/#urls" target="_blank">URLs</a> </li>
	    <li><a href="http://freiheit.f4.htw-berlin.de/webtech/html/#domain-name-service-dns" target="_blank">Domain Name Service (DNS)</a> </li>
	</ul>
	</body>
	</html>
	```

??? question "Woche 3 - Cascading Style Sheets (CSS)"
	- siehe [**CSS**](./css/#css)
	- siehe **Übungsaufgabe 2 (CSS)**
	- <iframe src="https://mediathek.htw-berlin.de/media/embed?key=3aaeac8e5d171874bdd0933e776165c4&width=720&height=450&autoplay=false&autolightsoff=false&loop=false&chapters=false&related=false&responsive=false&t=0" data-src="" class="iframeLoaded" width="720" height="450" frameborder="0" allowfullscreen="allowfullscreen" allowtransparency="true" scrolling="no"></iframe>

??? "css.html aus CSS-Vorlesung"
	```html
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>CSS</title>
	    <!-- 1. externe CSS-Datei -->
	    <link rel="stylesheet" href="./styles/mystyles.css">
	    <!-- 2. style-Element -->
	    <style>
	        h1 {
	            font-weight: normal;
	            color: red;
	        }

	        div > ul {
	            color: grey;
	        }

	        li {
	            display: inline;
	            padding: 10px;
	            margin: 5px;
	        }

	        span {
	            display: block;
	            color: red;
	        }

	    </style>
	</head>
	<body>
	    <h1>Cascading Style Sheets (CSS)</h1>
	    <div>living standard - weiterentwickelt von W3C. <span>Seit 2000 CSS3.</span>
	        Wichtig: Trennung zwischen Inhalten (HTML) und Aussehen (CSS).
	    </div>
	    <div> Wofür CSS?
	        <section>
	         <ul class="orangeBackground blackColor">
	             <li>ansprechender Stil (Font, Farben, Schriftgröße, Rahmen, ...)
	                 <a href="index.html">Link 2</a>
	             </li>
	             <li>Layout (2-spaltig, 3-spaltig, Kopf- und Fußzeilen, ...)
	                 <a href="index.html">Link 3</a>
	             </li>
	             <li>responsives Webdesign (unterschiedlich für Mobile, Tablets, Desktop, ...)
	                 <a href="index.html">Link 4</a>
	             </li>
	         </ul>
	        </section>
	    </div>
	    <ul class="orangeBackground">Inhalte heute:
	        <li>Orte für CSS-Definitionen
	            <a href="Unter/dok1.html">Link 5</a>
	        </li>
	        <li>Selektoren
	            <a href="Unter/dok1.html">Link 6</a>
	        </li>
	        <li>Box Model
	            <a href="Unter/dok1.html">Link 7</a>
	        </li>
	        <li>Layout (Prinzip, float)
	            <a href="Unter/dok1.html">Link 8</a>
	        </li>
	        <li>Gewichtung der Selektoren
	            <a href="Unter/dok1.html">Link 9</a>
	        </li>
	    </ul>
	</body>
	</html>
	```
??? "styles/mystyles.css aus CSS-Vorlesung"
	```css
	/*
	Kommentar in CSS

	selektor {
	    eigenschaft1: wert;
	    eigenschaft2: wert;
	   }
	*/

	body {
	    font-family: Verdana;
	    color: blue;
	}

	a {
	    text-decoration: none;
	    color: sandybrown;
	}
	```
??? "layout.html aus CSS-Vorlesung"
	```html
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>Layout mit float</title>
	    <style>
	        #p1, #p2, #p3 {
	            float: left;
	            width: 31.33%;
	            padding: 1%;
	        }
	    </style>
	</head>
	<body>
	    <p id="p1"><img src="./images/fiw.jpg" alt="fiw-logo" style="width:100%;"/></p>
	    <p id="p2">Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy
	        eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam
	        voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet
	        clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit
	        amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam
	        nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat,
	        sed diam voluptua. At vero eos et accusam et justo duo dolores et ea
	        rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem
	        ipsum dolor sit amet.</p>
	    <p id="p3">Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy
	        eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam
	        voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet
	        clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit
	        amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam
	        nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat,
	        sed diam voluptua. At vero eos et accusam et justo duo dolores et ea
	        rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem
	        ipsum dolor sit amet.</p>
	</body>
	</html>
	```
??? "gewichtung.html aus CSS-Vorlesung"
	```html
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>Gewichtung der Selektoren</title>
	    <style>
	        a:link { /* B=0  C=1 D=1 */
	            color: blue;
	        }
	        li a {  /* B=0 C=0 D=2 */
	            color: magenta;
	        }
	        #navigation a.link { /* B=1 C=1 D=1 */
	            color: red;
	        }
	        #navigation li a { /* B=1 C=0 D=2 */
	            color: black;
	        }
	    </style>
	</head>
	<body>
	<ul id="navigation">
	    <li><a href="startseite.html" class="link">Startseite</a></li>
	    <li><a href="unterseite.html" class="link">Unterseite</a></li>
	    <li> Kategorie A: style-Attribut im html-Element (Beispiel 0)</li>
	    <li> Kategorie B: für id</li>
	    <li> Kategorie C: Anzahl Klassen und Pseudoklassen</li>
	    <li> Kategorie D: Anzahl der Elemente und Pseudoelemente</li>
	</ul>
	</body>
	</html>
	```

??? question "Woche 4 - Responsive Webdesign (RWD)"
	- siehe [**Responsive Webdesign**](./rwd/#responsive-web-design)
	- siehe **Übungsaufgabe 3 (RWD + Bootstrap)**
	- <iframe src="https://mediathek.htw-berlin.de/media/embed?key=f5fb8d51009c1106b925a2d42d42ddc1&width=720&height=450&autoplay=false&autolightsoff=false&loop=false&chapters=false&related=false&responsive=false&t=0" data-src="" class="iframeLoaded" width="720" height="450" frameborder="0" allowfullscreen="allowfullscreen" allowtransparency="true" scrolling="no"></iframe>

??? question "Woche 5 - JavaScript (DOM)"
	- siehe [**JavaScript**](./javascript/#javascript)
	- siehe **Übungsaufgabe 4 (JavaScript, DOM)**
	- <iframe src="https://mediathek.htw-berlin.de/media/embed?key=0ae493c2d44631540aae98380fce7e58&width=720&height=529&autoplay=false&autolightsoff=false&loop=false&chapters=false&related=false&responsive=false&t=0" data-src="" class="iframeLoaded" width="720" height="529" frameborder="0" allowfullscreen="allowfullscreen" allowtransparency="true" scrolling="no"></iframe>

??? "javascript.html aus JavaScript (DOM)-Vorlesung"
	```html
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <meta name="viewport" content="width=device-width, initial-scale=1">
	    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.5.3/dist/css/bootstrap.min.css" integrity="sha384-TX8t27EcRE3e/ihU7zmQxVncDAy5uIKz4rEkgIXeMed4M0jlfIDPvg6uqKI2xXr2" crossorigin="anonymous">
	    <title>HTML ändern</title>
	</head>
	<body class="container-fluid">
	    <input id="input1" type="text" class="form-control" placeholder="neues Item" onchange="doSomething()"/>
	    <ul id = "ul1" class="list-group">
	        <li class="list-group-item active">erster</li>
	        <li class="list-group-item">zweiter</li>
	        <li class="list-group-item">dritter</li>
	    </ul>
	    <button type="button" class="btn btn-primary" onclick="createHeadline()">Klick mich</button>
	    <script>
	        var idnr = 1;
	        function doSomething()
	        {
	            let input1 = document.getElementById('input1');
	            let input1_value = input1.value;
	            let ul1 = document.getElementById('ul1');
	            let new_item = document.createElement('li');
	            new_item.classList.add("list-group-item");
	            new_item.id = "li" + idnr++;
	            /*
	            let new_text = document.createTextNode(input1_value);
	            new_item.appendChild(new_text);     // li --> value
	             */
	            new_item.innerHTML = input1_value + "<span style='color: red;'> test </span>";
	            let listitems = document.getElementsByTagName('li');

	            console.log("--------- drei ---------" + listitems.length);
	            for(let i=0; i<listitems.length; i++)
	            {
	                console.log(listitems[i]);
	            }
	            ul1.insertBefore(new_item, listitems[0]);
	            let new_item2 = document.createElement('li');
	            new_item2.classList.add("list-group-item");
	            new_item2.id = "li" + idnr++;
	            new_item2.innerHTML = "fuenftes";
	            ul1.appendChild(new_item2);

	            console.log("--------- nach 2 neuen ---------" + listitems.length);
	            for(let i=0; i<listitems.length; i++)
	            {
	                console.log(listitems[i]);
	            }
	            listitems[1].classList.remove("active");
	            listitems[3].classList.add("active");
	        }

	        function createHeadline()
	        {
	            let body = document.body;
	            let input = document.getElementById('input1');
	            let h1 = document.createElement('h1');
	            h1.innerHTML = "HTML ändern";
	            h1.addEventListener('mouseover', doSomethingElse);
	            h1.addEventListener('mouseout', doSomethingElse);
	            body.insertBefore(h1, input);
	        }

	        function doSomethingElse(event)
	        {
	            let h1 = event.target;
	            if(h1.style.color === "red")
	            {
	                h1.style.color = "green";
	                h1.style.fontSize = "xx-large";
	                h1.innerHTML = "... und weg";
	            }
	            else {
	                h1.style.color = "red";
	                h1.style.fontSize = "400%";
	                h1.innerHTML = "... und wieder da";
	            }
	        }
	    </script>
	</body>
	</html>
	```


??? question "Woche 6 - JavaScript (JSON, Ajax)"
	- siehe [**JSON**](./json/#javascript-object-notation-json) und [**Ajax**](./json/#ajax)
	- siehe **Übungsaufgabe 5 (JSON, Ajax)**
	- <iframe src="https://mediathek.htw-berlin.de/media/embed?key=8d22ab3fc07dd403c6a66849c34f6f9b&width=720&height=450&autoplay=false&autolightsoff=false&loop=false&chapters=false&related=false&responsive=false&t=0" data-src="" class="iframeLoaded" width="720" height="450" frameborder="0" allowfullscreen="allowfullscreen" allowtransparency="true" scrolling="no"></iframe>

??? "json+ajax.html aus JavaScript (JSON, Ajax)-Vorlesung"
	```html
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>JSON+AJAX</title>
	</head>
	<body onload="loadJSON()">
	<h3>Objekte</h3>
	<div id="div1"></div>
	<button type="button" onclick="showObjects()">Show Objects</button>
	<script>
	    let person_obj;

	    function showObjects()
	    {
	        /*
	        let person = {
	            vorname: "Maria",
	            nachname: "Musterfrau",
	            kinder: {
	                max: {
	                    vorname: "Max",
	                    alter: 7
	                },
	                moritz: {
	                    vorname: "Moritz",
	                    alter: 3
	                }
	            },
	            auskunft: function() {
	                return "F: " + this.vorname + " " + this.nachname;
	            }
	        }
	        console.log(person.auskunft());

	        person.wohnort = "Musterdorf";
	        */
	        let person = person_obj;

	        console.log(person);
	        console.log(person.vorname + " " + person.nachname);
	        document.getElementById('div1').innerHTML += person.vorname + " " + person.nachname + "<br/>";
	        console.log(person.wohnort);

	        /*
	        let kinder = person.kinder;
	        for(let i=0; i<kinder.length; i++)
	        {
	            console.log(kinder[i].vorname);
	        }

	         */
	        console.log(person.kinder.max.vorname);
	        console.log(person.kinder.moritz.vorname);

	        for(let eigenschaften in person)
	        {
	            console.log(eigenschaften);
	            console.log(person[eigenschaften]);
	        }

	        for(let eigenschaften in person.kinder)
	        {
	            console.log(person.kinder[eigenschaften].vorname);
	            for(let kidseig in person.kinder[eigenschaften])
	            {
	                console.log(person.kinder[eigenschaften][kidseig]);
	            }
	        }

	        let json_obj = JSON.stringify(person);
	        document.getElementById('div1').innerHTML += json_obj;
	    }

	    function loadJSON()
	    {
	        let xhttp = new XMLHttpRequest();
	        xhttp.onreadystatechange = function() {
	            if(this.readyState === 4 && this.status === 200)
	            {
	                person_obj = JSON.parse(this.responseText);
	                showObjects();
	            }
	        };
	        xhttp.open("GET", "http://localhost/Webtech20/person.json", true);
	        xhttp.send();
	    }
	</script>
	</body>
	</html>
	```

??? "person.json aus JavaScript (JSON, Ajax)-Vorlesung"
	```json
	{
	  "vorname": "Maria",
	  "nachname": "Musterfrau",
	  "kinder": {
	    "max": {
	      "vorname": "Max",
	      "alter": 7
	    },
	    "moritz": {
	      "vorname": "Moritz",
	      "alter": 3
	    }
	  },
	  "wohnort": "Musterdorf"
	}
	```

??? question "Woche 7 - Angular (erstes Angular-Projekt)"
	- Diese Woche geht es darum, dass für alle die gesamte Entwicklungsumgebung (`npm`, `ng`) so funktioniert, dass Sie sich ein erstes Angular-Projekt aufsetzen können. Es gibt deshalb auch kein Video, weil ich da nur zeigen würde, wie ich das Projekt aufsetze. Arbeiten Sie die Übungsaufgabe 6 ([die Übungen wurden verschoben](./uebungen/#ubungen)) ab. Wenn alles klappt, sollte es schnell gehen. Ich werde in der Übung am 24.11. die Durchführung der Übung 6 zeigen und dabei ein Video aufnehmen, das ich hier einstelle.
	- siehe **Übungsaufgabe 6**
	- siehe [**Angular**](./angular/#angular)

??? question "Woche 8 - Angular (Material und Routing)"
	- Wir erweitern das Frontend. Wir nutzen Material als CSS-Framework. Wir verwenden das Tables-Schema, um eine Tabelle unserer Mockup-Daten zu erstellen und implementieren ein kleines Formular. Wir führen Routing ein, auch parametrisiertes Routing. Es wird ein Service erstellt, der sich um die (client-seitige) Verwaltung der Daten kümmert und der allen Komponenten zur Verfügung steht. 
	- Es gibt kein Video, da der Abschnitt [Material](./material/#material-fur-angular) vollständig als Schritt-für-Schritt-Anleitung geschrieben wurde. 
	- die **Übungsaufgabe 7** besteht darin, diesen Abschnitt Schritt für Schritt nachzuvollziehen. 

??? question "Woche 9 - Node.js + Express (REST-Server + MySQL)"
	- Wir erstellen ein Backend. Wir nutzen Node.js und Express, um einen REST-Server zu implementieren, der uns alle CRUD-Funktionalitäten für die Verwaltung unseres Mockup-Datensatzes zur Verfügung stellt. Wir verwenden MySQL zur Speicherung unserer Mockup-Daten. Der REST-Server enthält ein Model und einen Controller.  
	- Es gibt kein Video, da der Abschnitt [REST-API](./backend/#rest-api) vollständig als Schritt-für-Schritt-Anleitung geschrieben wurde. 
	- die **Übungsaufgabe 8** besteht darin, diesen Abschnitt Schritt für Schritt nachzuvollziehen. 

??? question "Woche 10 - Angular - Anbindung ans Backend I"
	- Wir erstellen ein Frontend, mit dem wir an das im Abschnitt [REST-API](./backend/#rest-api) Backend anbinden. Wir beginnen mit dem Auslesen aller Datensätze und lesen dann auch noch einen einzelnen Datensatz aus. Es werden also die Backend-Endpunkte `GET localhost:3000/members` und `GET localhost:3000/members/id` angebunden. Dazu machen wir uns mit dem `HttpClient` vertraut und lernen `Observable`s kennen. Wir erstellen unter Verwendung von Bootstrap eine Tabelle und ein Formular und nutzen Bootstrap-Icons. Wir untersuchen, wie man den Datenfluss von Eltern- auf Kindkomponenten realisiert und verwenden Interpolation sowie Strukturdirektiven.   
	- Es gibt kein Video, da der Abschnitt [Anbindung an das Backend](./backendanbindung/#anbindung-an-das-backend) vollständig als Schritt-für-Schritt-Anleitung mit zusätzlichen Erläuterungen und Links geschrieben wurde. 
	- die **Übungsaufgabe 9** besteht darin, diesen Abschnitt Schritt für Schritt nachzuvollziehen. 

??? question "Woche 11 - Angular - Anbindung ans Backend II"
	- Wir schließen die Anbindung an das im Abschnitt [REST-API](./backend/#rest-api) erstellte Backend ab und erstellen die fehlenden Funktionalitäten `delete` und `create`. Dazu erstellen wir für `delete` einen modalen Dialog. 
	- Es gibt kein Video, da der Abschnitt [Anbindung an das Backend](./backendanbindung/#anbindung-an-das-backend) vollständig als Schritt-für-Schritt-Anleitung mit zusätzlichen Erläuterungen und Links geschrieben wurde. 
	- die **Übungsaufgabe 10** besteht darin, diesen Abschnitt Schritt für Schritt nachzuvollziehen. 

---

*Bis hier haben Sie alles, was Sie für Ihre Semesteraufgabe benötigen, wenn Sie sie alleine erstellen. Ab hier ist alles Zusatz, müssen Sie also nicht mehr machen.*

---

??? question "Woche 12 - JSON Web Token (JWT)"
	- wir erstellen uns ein Frontend und ein Backend für die Registrierung und das Login mithilfe von JWT
	- das dazugehörige Skript finden Sie unter [JSON Web Tokens (JWT)](./jwt/#json-web-tokens-jwt)
	- die **Übungsaufgabe 11** besteht darin, diesen Abschnitt Schritt für Schritt nachzuvollziehen. Sie können auch zusätzlich gerne die dort im [Ausblick](./jwt/#ausblick) diskutierten fehlenden Fehlerreaktionen implementieren - müssen Sie aber auch nicht.

## Semesteraufgabe

Am Ende des Kurses geben Sie eine Webanwendung ab. Diese wird bewertet und bildet die Modulnote für "WebTech" (es gibt also keine Klausur o.ä.). Überlegen Sie sich früh, was Sie implementieren wollen. Ihrer Kreativität sind keine Grenzen gesetzt. Es können 2 Studentinnen gemeinsam ein Projekt durchführen und abgeben. Sie erhalten dann (höchstwahrscheinlich) die gleiche Note. Es muss an den Commits erkennbar sein, welchen Anteil am Ergebnis jede der beiden Studentinnen hatte.

*Sobald Sie mit Ihrem Semesterprojekt fertig sind, geben Sie mir bitte Bescheid! Wir vereinbaren dann einen Online-Gesprächstermin. Sie müssen auch im 2.PZ nicht bis zum 1.4. warten - im Gegenteil, wenn wir die Gespräche in den März legen können, um so besser.*

??? question "Mindestanforderungen"
	Folgende Anforderungen werden an Ihr Projekt gestellt:

	* das Frontend soll mit Angular entwickelt werden,
	* das Backend mit Node.js,
	* als Datenbank soll MySQL verwendet werden,
	* es soll CRUD implementiert sein, d.h. Sie benötigen 
	    * eine Komponente zur Erstellung und Speicherung eines Datenbankeintrages (<b>C</b>reate),
	    * eine Komponente zur Änderung eines Datenbankeintrages (<b>U</b>pdate),
	    * eine Komponente zur Anzeige *aller* Datenbankeinträge (<b>R</b>ead),
	    * eine Komponente zum Löschen eines Datenbankeintrages (<b>D</b>elete).
    * wenn Sie die Anwendung alleine umsetzen, dann genügen 3 der 4 CRUD-Funktionalitäten
    * wenn Sie die Anwendung zu zweit entwickeln, dann
    	* sollen alle 4 CRUD-Funktionalitäten umgesetzt werden und
    	* Login (Username + Passwort) und
    	* ich schaue mir die Commit-Hiostorie im Git genauer an, um sicherzugehen, dass beide Studentinnen gleich viel an der Anwendung mitentwickelt haben

	Datenbankeinträge können Bücher, CDs, ToDos, Einkaufslisten, Vorlesungen, Kühlschrankinhalte usw. sein - wie gesagt, Ihrer Kreativität sind keine Grenzen gesetzt. 

	Die Anwendung soll in einem Git-Dienst (GitHub, GitLab, ...) verfügbar sein. Das README (oder eine andere Form der Projektbeschreibung) soll aussagekräftig sein.

	Verwenden Sie ein CSS-Framework, wie z.B. Materialize, Bootstrap o.ä.! Ihre Anwendung soll "modern" aussehen. 

	Nach Abgabe vereinbaren wir ein Online-Meeting, in dem Sie mir Ihre Anwendung nochmal zeigen können und ich Ihnen Fragen zu Ihrem Code stellen werde. Ist keine Prüfung, sondern eher ein fachliches Gespräch. 
