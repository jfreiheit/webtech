# Web-Technologien

Herzlich willkommen zur WebTech-Veranstaltung! 

### Grober Inhalt

In dieser Veranstaltung lernen Sie, was das World Wide Web ist und wie man eigene Webseiten und -anwendungen realisiert. Sie lernen die Protokolle und Sprachen ``http``, ``HTML``, ``CSS``und ``JavaScript`` kennen und machen sich mit ``Angular``, ``Node.js`` und ``REST`` vertraut.  

| | Woche | Themen (Vorlesung) | Übung | Aufgabe (Stand) | Abgabe Übung bis | 
|-|-------|--------------------|-------|-----------------|------------------|
| 1. | 05.-09.10.2020 | Einführung und Organsitorisches | Übung 0 | - | - | 
| 3. | 12.-16.10.2020 | HTML | Übung 1 | Idee | 25.10.2020 | 
| 4. | 19.-23.10.2020 | CSS (Eigenschaften und Selektoren) | Übung 2 | - | 01.11.2020 | 
| 5. | 26.-30.10.2020 | CSS (Layout und Responsive Webdesign) | Übung 3 | Konzept | 08.11.2020 | 
| 6. | 02.-06.11.2020 | Angular (Einführung und Komponenten) | Übung 4 | - | 15.11.2020 | 
| 7. | 09.-13.11.2020 | Angular (Direktiven, data-, property-, event-binding) | Übung 5 | Datenmodell | 22.11.2020 | 
| 8. | 16.-20.11.2020 | Angular (Lifecycle-Hooks, Services, Routing) | Übung 6 | Schnittstelle | 29.11.2020 | 
| 9. | 23.-27.11.2020 | Angular (HTTP-Client), MySQL, REST | Übung 7 | Frontend (c+r)| 06.12.2020 | 
| 10. | 30.-04.12.2020 | Angular (Formulare) | Übung 8 | Frontend (u+d)| 13.12.2020 | 
| 11. | 07.-11.12.2020 | Node.js (Einführung, Webserver) | Übung 9 | Frontend fertig | 20.12.2020 | 
| 12. | 14.-18.12.2020 | Node.js (Express, Request, Response, URL) | Übung 10 | Backend (c) | 10.01.2020 | 
| 13. | 21.-25.12.2020 | Node.js (Model View Controller), JSON | - | Backend (r) | - |
| 14. | 04.-08.01.2021 | Node.js (Datenbankanbindung, REST-Server) | - | Backend (u) | - |
| 15. | 11.-15.01.2021 | JSON Web Tokens | - | Backend (d + fertig)| - |
| 16. | 18.-22.01.2021 | Wiederholung | - | fertig stellen | - |
| 17. | 25.-29.01.2021 | - | Fragen | Abgabe 1.PZ 13.02.2021 | - |
|  |  |  |  | Abgabe 2.PZ 01.04.2021 | - |

### Organisatorisches 

Zur erfolgreichen Durchführung der Veranstaltung müssen die Übungen lösen und zu den jeweiligen Fristen per Git auf einen Server (GitHub oder GitLab) laden. Am Ende des Semesters ist eine Aufgabe abzugeben. Diese Aufgabe wird bewertet. Die Bewertung entspricht dann der Modulnote. 

Hier sind die Übungen beschrieben, die Sie in jeder Woche ausführen sollen. Damit Sie dies erfolgreich erledigen können, ist jeweils angegeben, welche Themen Sie dafür durcharbeiten müssen. Das Durcharbeiten der jeweiligen Themen entspricht jeweils einer Vorlesung. Diese wird also selbständig durchgeführt. 

Für die Kommunikation untereinander verwenden wir [**Slack**](https://slack.com/intl/de-de/). Dort können Sie alle inhaltlichen und organisatorischen Fragen stellen. Ich fände es gut, wenn ich dort möglichst wenig Fragen - zumindest die inhaltlichen - beantworten müsste, sondern eine Art internes Diskussionsforum entsteht. Es ist sehr gewünscht, dort Fragen zu stellen und noch mehr gewünscht, diese von Ihnen dort beantwortet zu sehen. Damit wäre allen geholfen und ich kann besser erkennen, wo noch Nachhol- bzw. Erläuterungsbedarf bei den meisten besteht.  

### Wochenplan

??? question "Woche 1 - Einführung und Organisatorisches"
	- siehe **Übungsaufgabe 0**
	- 01_Einführung
		<video controls="controls" width="200">
  		<source type="video/mp4" src="./files/videos/01_Einfuehrung.mp4"></source>
  		<p>Your browser does not support the video element.</p>
	  </video>
	- die Notizen dazu finden Sie [**hier**](./files/01_WebTech_Einfuehrung.pdf)
	- 02_Organisatorisches
	 	<video controls="controls" width="200">
  		<source type="video/mp4" src="./files/videos/02_Organisatorisches.mp4"></source>
  		<p>Your browser does not support the video element.</p>
		</video>
	- die Notizen dazu finden Sie [**hier**](./files/02_Organisatorisches.pdf)

??? question "Woche 2 - Hypertext Markup Language (HTML)"
	- siehe **Übungsaufgabe 1**
	- 03_HTML
		<video controls="controls" width="200">
  		<source type="video/mp4" src="./files/videos/03_HTML.mp4"></source>
  		<p>Your browser does not support the video element.</p>
	  </video>
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

## Übungen

??? question "Übungsaufgabe 0"
    - wählen Sie eine [**IDE**](./tools/#integrated-development-environment-ide) aus und installieren Sie diese 
    - richten Sie sich ein Git-Repository ein (z.B. ``WebTech20``) und pushen Sie es auf einen zentralen Dienst ([**siehe**](./tools/#git))
    - laden Sie mich zu Ihrem Git-Dienst ein ([**siehe**](./tools/#git))
    - erstellen Sie in Ihrem Repostory eine Datei ``index.php`` mit folgendem Inhalt: ``<?php phpinfo(); ?>``
    - richten Sie Ihren Webserver so ein, dass ``WebTech20`` Ihr *DocumentRoot* ist ([**siehe**](./tools/#webserver))
    - commiten und pushen Sie Ihr Repository

??? question "Übungsaufgabe 1"
	- Erstellen Sie in einem `Uebung1`-Ordner eine Datei `uebung1.html`. Das `body`-Element soll ein `header`-Element, ein `nav`-Element, ein `section`-Element und ein `footer`-Element enthalten. 
	- Unter dieser Übungsaufgabe (siehe `mockupdata`) ist der HTML-Code einer Tabelle mit allen Teilnehmerinnen einer Veranstaltung. Kopieren Sie den Inhalt der Datei so in Ihren HTML-Code, dass folgende Seite erscheint:

	![Uebung1](./files/49_uebung1.png)

	- Es sollen 4 Unterseiten erstellt werden. Bei Klick auf diese Seiten soll die Tabelle jeweils nur die Teilnehmerinnen enthalten, deren Nachname mit dem entsprechenden Anfangsbuchstaben beginnt. Die Seiten `ag.html`, `hl.html`, `mr.html` und `sz.html` sollen im Ordner `NN` abgelegt werden, der Unterordner von `Uebung1` ist.
	- Achten Sie darauf, dass man von jeder Unterseite auf jede andere Unterseite und auch auf die Hauptseite (`uebung1.html`) wechseln können muss.
	- Das einzubindende Logo des Studiengangs liegt [hier](./files/fiw.jpg). Es soll in einen `images`-Ordner gespeichert werden, der in der Ordner-Hierarchie neben dem `Uebung1`-Ordner liegt. Um die Größe des Bildes festzulegen, können Sie mit Hilfe des `style`-Attributes die Höhe und die Breite bestimmen: `style="width:53px; height=48px;"` 
	- Nächste Woche wird Uebung1 um CSS erweitert. 


??? "mockupdata"
	```html
	<table>
		<thead>
			<tr>
				<th>Vorname</th>
				<th>Nachname</th>
				<th>E-Mail-Adresse</th>
				<th>IP-Adresse</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>Adam</td>
				<td>Anderson</td>
				<td>aanderson8@google.fr</td>
				<td>118.93.83.157</td>
			</tr>
			<tr>
				<td>Susan</td>
				<td>Andrews</td>
				<td>sandrewsn@google.co.jp</td>
				<td>228.214.9.251</td>
			</tr>
			<tr>
				<td>Catherine</td>
				<td>Andrews</td>
				<td>candrewsp@noaa.gov</td>
				<td>112.111.87.178</td>
			</tr>
			<tr>
				<td>Alan</td>
				<td>Bradley</td>
				<td>abradley1c@globo.com</td>
				<td>229.152.117.127</td>
			</tr>
			<tr>
				<td>Anne</td>
				<td>Brooks</td>
				<td>abrooks16@bravesites.com</td>
				<td>243.159.39.234</td>
			</tr>
			<tr>
				<td>Russell</td>
				<td>Brown</td>
				<td>rbrownq@nifty.com</td>
				<td>215.38.120.242</td>
			</tr>
			<tr>
				<td>Ryan</td>
				<td>Burton</td>
				<td>rburton18@foxnews.com</td>
				<td>159.60.107.14</td>
			</tr>
			<tr>
				<td>Roy</td>
				<td>Campbell</td>
				<td>rcampbell1@geocities.com</td>
				<td>237.232.34.20</td>
			</tr>
			<tr>
				<td>Russell</td>
				<td>Campbell</td>
				<td>rcampbell17@eventbrite.com</td>
				<td>251.2.92.63</td>
			</tr>
			<tr>
				<td>Bonnie</td>
				<td>Coleman</td>
				<td>bcoleman11@fc2.com</td>
				<td>109.150.122.102</td>
			</tr>
			<tr>
				<td>Ernest</td>
				<td>Coleman</td>
				<td>ecoleman15@businessweek.com</td>
				<td>213.173.4.7</td>
			</tr>
			<tr>
				<td>Richard</td>
				<td>Cruz</td>
				<td>rcruz7@unc.edu</td>
				<td>235.124.23.221</td>
			</tr>
			<tr>
				<td>Sean</td>
				<td>Cruz</td>
				<td>scruz10@answers.com</td>
				<td>92.255.49.227</td>
			</tr>
			<tr>
				<td>Rebecca</td>
				<td>Cunningham</td>
				<td>rcunninghamd@mac.com</td>
				<td>65.79.191.52</td>
			</tr>
			<tr>
				<td>Margaret</td>
				<td>Evans</td>
				<td>mevansh@pcworld.com</td>
				<td>162.10.86.196</td>
			</tr>
			<tr>
				<td>Jeffrey</td>
				<td>Ford</td>
				<td>jford14@cnet.com</td>
				<td>210.216.54.14</td>
			</tr>
			<tr>
				<td>Andrea</td>
				<td>Gardner</td>
				<td>agardnerv@woothemes.com</td>
				<td>179.91.0.30</td>
			</tr>
			<tr>
				<td>Deborah</td>
				<td>George</td>
				<td>dgeorge6@furl.net</td>
				<td>201.76.47.162</td>
			</tr>
			<tr>
				<td>Sean</td>
				<td>Gibson</td>
				<td>sgibsony@alexa.com</td>
				<td>48.114.103.55</td>
			</tr>
			<tr>
				<td>Virginia</td>
				<td>Graham</td>
				<td>vgrahamk@aol.com</td>
				<td>165.219.171.1</td>
			</tr>
			<tr>
				<td>Steven</td>
				<td>Hamilton</td>
				<td>shamiltonu@state.tx.us</td>
				<td>38.194.91.201</td>
			</tr>
			<tr>
				<td>Virginia</td>
				<td>Hawkins</td>
				<td>vhawkinsf@ehow.com</td>
				<td>93.120.46.203</td>
			</tr>
			<tr>
				<td>Edward</td>
				<td>Hicks</td>
				<td>ehicksc@pcworld.com</td>
				<td>199.153.27.1</td>
			</tr>
			<tr>
				<td>Mark</td>
				<td>Johnson</td>
				<td>mjohnsonj@hostgator.com</td>
				<td>73.87.135.206</td>
			</tr>
			<tr>
				<td>Ruth</td>
				<td>Jordan</td>
				<td>rjordan1a@smugmug.com</td>
				<td>193.140.80.64</td>
			</tr>
			<tr>
				<td>Antonio</td>
				<td>Kim</td>
				<td>akim4@odnoklassniki.ru</td>
				<td>168.244.191.78</td>
			</tr>
			<tr>
				<td>Jennifer</td>
				<td>Marshall</td>
				<td>jmarshallt@gnu.org</td>
				<td>104.191.49.94</td>
			</tr>
			<tr>
				<td>Eric</td>
				<td>Matthews</td>
				<td>ematthews5@independent.co.uk</td>
				<td>138.194.30.1</td>
			</tr>
			<tr>
				<td>Raymond</td>
				<td>Mcdonald</td>
				<td>rmcdonald2@ihg.com</td>
				<td>161.24.42.24</td>
			</tr>
			<tr>
				<td>Eric</td>
				<td>Miller</td>
				<td>emillere@creativecommons.org</td>
				<td>122.159.17.218</td>
			</tr>
			<tr>
				<td>Jonathan</td>
				<td>Morales</td>
				<td>jmoralesa@ovh.net</td>
				<td>97.65.110.105</td>
			</tr>
			<tr>
				<td>Marie</td>
				<td>Morgan</td>
				<td>mmorganb@cloudflare.com</td>
				<td>226.79.152.112</td>
			</tr>
			<tr>
				<td>Amanda</td>
				<td>Nelson</td>
				<td>anelson13@indiatimes.com</td>
				<td>161.185.121.245</td>
			</tr>
			<tr>
				<td>Lisa</td>
				<td>Olson</td>
				<td>lolsonr@telegraph.co.uk</td>
				<td>77.245.172.100</td>
			</tr>
			<tr>
				<td>Alice</td>
				<td>Ortiz</td>
				<td>aortizw@histats.com</td>
				<td>179.52.222.21</td>
			</tr>
			<tr>
				<td>Peter</td>
				<td>Phillips</td>
				<td>pphillipss@1688.com</td>
				<td>11.158.255.76</td>
			</tr>
			<tr>
				<td>Matthew</td>
				<td>Porter</td>
				<td>mporter9@europa.eu</td>
				<td>174.81.178.88</td>
			</tr>
			<tr>
				<td>Tammy</td>
				<td>Ray</td>
				<td>trayx@weather.com</td>
				<td>192.243.38.190</td>
			</tr>
			<tr>
				<td>Mark</td>
				<td>Richardson</td>
				<td>mrichardson1d@ihg.com</td>
				<td>209.217.14.154</td>
			</tr>
			<tr>
				<td>Joan</td>
				<td>Roberts</td>
				<td>jroberts12@alibaba.com</td>
				<td>4.91.143.62</td>
			</tr>
			<tr>
				<td>Kathleen</td>
				<td>Rose</td>
				<td>kroseg@pinterest.com</td>
				<td>222.172.140.56</td>
			</tr>
			<tr>
				<td>Steve</td>
				<td>Sanders</td>
				<td>ssanders1b@wikispaces.com</td>
				<td>91.61.109.245</td>
			</tr>
			<tr>
				<td>Shirley</td>
				<td>Scott</td>
				<td>sscottm@macromedia.com</td>
				<td>219.237.108.82</td>
			</tr>
			<tr>
				<td>Lillian</td>
				<td>Stephens</td>
				<td>lstephens19@hugedomains.com</td>
				<td>89.85.137.204</td>
			</tr>
			<tr>
				<td>Nicole</td>
				<td>Thompson</td>
				<td>nthompson3@admin.ch</td>
				<td>13.183.208.155</td>
			</tr>
			<tr>
				<td>Marie</td>
				<td>Thompson</td>
				<td>mthompsonz@yelp.com</td>
				<td>162.164.5.231</td>
			</tr>
			<tr>
				<td>Alan</td>
				<td>Vasquez</td>
				<td>avasquezo@miibeian.gov.cn</td>
				<td>178.109.86.172</td>
			</tr>
			<tr>
				<td>Mildred</td>
				<td>Watkins</td>
				<td>mwatkins0@miibeian.gov.cn</td>
				<td>150.67.132.64</td>
			</tr>
			<tr>
				<td>Eugene</td>
				<td>Williams</td>
				<td>ewilliamsi@deliciousdays.com</td>
				<td>67.208.26.182</td>
			</tr>
			<tr>
				<td>Catherine</td>
				<td>Williams</td>
				<td>cwilliamsl@360.cn</td>
				<td>154.87.204.51</td>
			</tr>
		</tbody>
	</table>
	```

??? question "Übungsaufgabe 4 - wird aber noch geändert!"
    Arbeiten Sie im Abschnitt [**Angular**](./angular/#angular) die Abschnitte [**Erstes Projekt erstellen**](./angular/#erstes-projekt-erstellen) und [**Angular-Projektstruktur**](./angular/#angular-projektstruktur) durch. Sie müssen dazu [**Angular**](./tools/#angular) installieren, eine [**Integrierte Entwicklungsumgebung**](./tools/#integrated-development-environment-ide) und die passenden [**Developer Tools**](./tools/#developer-tools). 


## Semesteraufgabe

Am Ende des Kurses geben Sie eine Webanwendung ab. Diese wird bewertet und bildet die Modulnote für "WebTech" (es gibt also keine Klausur o.ä.). Überlegen Sie sich früh, was Sie implementieren wollen. Ihrer Kreativität sind keine Grenzen gesetzt. Es können 2 Studentinnen gemeinsam ein Projekt durchführen und abgeben. Sie erhalten dann (höchstwahrscheinlich) die gleiche Note. Es muss an den Commits erkennbar sein, welchen Anteil am Ergebnis jede der beiden Studentinnen hatte.

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

	Datenbankeinträge können Bücher, CDs, ToDos, Einkaufslisten, Vorlesungen, Kühlschrankinhalte usw. sein - wie gesagt, Ihrer Kreativität sind keine Grenzen gesetzt. 

	Die Anwendung soll in einem Git-Dienst (GitHub, GitLab, ...) verfügbar sein. Das README (oder eine andere Form der Projektbeschreibung) soll aussagekräftig sein.

	Verwenden Sie ein CSS-Framework, wie z.B. Materialize, Bootstrap o.ä.! Ihre Anwendung soll "modern" aussehen. 
