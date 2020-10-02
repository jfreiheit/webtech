# Web-Technologien

Herzlich willkommen zur WebTech-Veranstaltung! 

### Grober Inhalt

In dieser Veranstaltung lernen Sie, was das World Wide Web ist und wie man eigene Webseiten und -anwendungen realisiert. Sie lernen die Protokolle und Sprachen ``http``, ``HTML``, ``CSS``und ``JavaScript`` kennen und machen sich mit ``Angular``, ``Node.js`` und ``REST`` vertraut.  

| | Woche | Themen (Vorlesung) | Übung | Aufgabe (Stand) |
|-|-------|--------------------|-------|-----------------|
| 1. | 05.-09.10.2020 | Einführung und Organsitorisches | Übung 1 | - |
| 3. | 12.-16.10.2020 | Webserver und HTML | Übung 2 | Idee |
| 4. | 19.-23.10.2020 | CSS (Eigenschaften und Selektoren) | Übung 3 | - |
| 5. | 26.-30.10.2020 | CSS (Layout und Responsive Webdesign) | Übung 4 | Konzept |
| 6. | 02.-06.11.2020 | Angular (Einführung und Komponenten) | Übung 5 | - |
| 7. | 09.-13.11.2020 | Angular (Direktiven, data-, property-, event-binding) | Übung 6 | Datenmodell |
| 8. | 16.-20.11.2020 | Angular (Lifecycle-Hooks, Services, Routing) | Übung 7 | Schnittstelle |
| 9. | 23.-27.11.2020 | Angular (HTTP-Client), MySQL, REST | Übung 8 | Frontend (c+r)|
| 10. | 30.-04.12.2020 | Angular (Formulare) | Übung 9 | Frontend (u+d)|
| 11. | 07.-11.12.2020 | Node.js (Einführung, Webserver) | Übung 10 | Frontend fertig |
| 12. | 14.-18.12.2020 | Node.js (Express, Request, Response, URL) | - | Backend (c) |
| 13. | 21.-25.12.2020 | Node.js (Model View Controller), JSON | - | Backend (r) |
| 14. | 04.-08.01.2021 | Node.js (Datenbankanbindung, REST-Server) | - | Backend (u) |
| 15. | 11.-15.01.2021 | JSON Web Tokens | - | Backend (d + fertig)|
| 16. | 18.-22.01.2021 | Wiederholung | - | fertig stellen |
| 17. | 25.-29.01.2021 | - | Fragen | Abgabe 1.PZ 13.02.2021 |
|  |  |  |  | Abgabe 2.PZ 01.04.2021 |

### Organisatorisches 

Zur erfolgreichen Durchführung der Veranstaltung müssen die Übungen lösen und zu den jeweiligen Fristen per Git auf einen Server (GitHub oder GitLab) laden. Am Ende des Semesters ist eine Aufgabe abzugeben. Diese Aufgabe wird bewertet. Die Bewertung entspricht dann der Modulnote. 

Hier sind die Übungen beschrieben, die Sie in jeder Woche ausführen sollen. Damit Sie dies erfolgreich erledigen können, ist jeweils angegeben, welche Themen Sie dafür durcharbeiten müssen. Das Durcharbeiten der jeweiligen Themen entspricht jeweils einer Vorlesung. Diese wird also selbständig durchgeführt. 

Für die Kommunikation untereinander verwenden wir [**Slack**](https://slack.com/intl/de-de/). Dort können Sie alle inhaltlichen und organisatorischen Fragen stellen. Ich fände es gut, wenn ich dort möglichst wenig Fragen - zumindest die inhaltlichen - beantworten müsste, sondern eine Art internes Diskussionsforum entsteht. Es ist sehr gewünscht, dort Fragen zu stellen und noch mehr gewünscht, diese von Ihnen dort beantwortet zu sehen. Damit wäre allen geholfen und ich kann besser erkennen, wo noch Nachhol- bzw. Erläuterungsbedarf bei den meisten besteht.  

### Wochenplan

??? question "Woche 1 - Einführung und Organisatorisches"
	- siehe **Übungsaufgabe 0**

## Übungen

??? question "Übungsaufgabe 0"
    - wählen Sie eine [**IDE**](./tools/#integrated-development-environment-ide) aus und installieren Sie diese 
    - richten Sie sich ein Git-Repository ein (z.B. ``WebTech20``) und pushen Sie es auf einen zentralen Dienst ([**siehe**](./tools/#git))
    - laden Sie mich zu Ihrem Git-Dienst ein ([**siehe**](./tools/#git))
    - erstellen Sie in Ihrem Repostory eine Datei ``index.php`` mit folgendem Inhalt: ``<?php phpinfo(); ?>``
    - richten Sie Ihren Webserver so ein, dass ``WebTech20`` Ihr *DocumentRoot* ist ([**siehe**](./tools/#webserver))
    - commiten und pushen Sie Ihr Repository


??? question "Übungsaufgabe 1"
    Arbeiten Sie im Abschnitt [**Angular**](./angular/#angular) die Abschnitte [**Erstes Projekt erstellen**](./angular/#erstes-projekt-erstellen) und [**Angular-Projektstruktur**](./angular/#angular-projektstruktur) durch. Sie müssen dazu [**Angular**](./tools/#angular) installieren, eine [**Integrierte Entwicklungsumgebung**](./tools/#integrated-development-environment-ide) und die passenden [**Developer Tools**](./tools/#developer-tools). 


## Aufgabe

Am Ende des Kurses geben Sie eine Webanwendung ab. Überlegen Sie sich früh, was Sie implementieren wollen. Ihrer Kreativität sind keine Grenzen gesetzt. Es können 2 Studentinnen gemeinsam ein Projekt durchführen und abgeben. Sie erhalten dann die gleiche Note. 

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

	Verwenden Sie ein CSS-Framework, wie z.B. Materialize, Bootstrap o.ä.! Ihre Anwendung soll modern aussehen. 
