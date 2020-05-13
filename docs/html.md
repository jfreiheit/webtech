# HTML

## Einleitung

HTML steht für <b>H</b>yper<b>T</b>ext <b>M</b>arkup <b>L</b>anguage. HTML ist eine sogenannte *Auszeichnungssprache*. Das bedeutet, dass Textelementen sogenannte *Tags* (HTML-Elemente) zugeordnet werden, um dem Text, der von einem solchen Tag umschlossen wird, eine Bedeutung zuzuweisen - der Text wird ausgezeichnet.

**Beispiel:**

``` HTML
<h1>Große Überschrift</h1>
```

Im obigen Beispiel wurde der Text Große Überschrift durch das HTML-Element `h1` ausgezeichnet. Die Bedeutung dieses Elementes ist, dass es sich bei dem ausgezeichneten Text um eine Überschrift handelt. Es gibt 6 HTML-Elemente, die Überschriften charakterisieren: `h1`, `h2`, `h3`, `h4`, `h5`, `h6`. Die Nummern geben die Größe der Überschrift an: `h1` ist die größte Überschrift, `h6` die kleinste. Klicken Sie im folgenden Fenster auf den Reiter **"Result"**, um die Unterschiede zu sehen:

<iframe width="100%" height="300" src="//jsfiddle.net/jfreiheit/fze5kd0L/2/embedded/html,css,result/" allowfullscreen="allowfullscreen" allowpaymentrequest="" frameborder="0"></iframe>


## Hierarchische Anordnung der HTML-Elemente

HTML-Elemente bestehen - bis auf wenige Ausnahmen - aus einem Start-Tag `<tag>` und einem Ende-Tag `</tag>` (tag steht hier für den Namen eines beliebigen Elementes). Wird ein neues HTML-Element `el2` innerhalb eines anderen HTML-Elementes `el1` geöffnet, so muss `el2` auch geschlossen werden, bevor `el1` geschlossen wird.  

!!! success
    ```html
    <el1> diese Anordnung der
        <el2>
              Elemente ist korrekt
        </el2>
    </el1>
    ```

!!! failure
    ```html
    <el1> diese Anordnung der
        <el2>
               Elemente ist falsch
    </el1>
       </el2>
    ```

Es gibt nur wenige HTML-Elemente, die nicht aus einem Start- und einem Ende-Tag bestehen, sondern sogenannte *stand-alone Tags* sind. Ein typisches Beispiel ist der Zeilenumbruch `<br>`. Um einerseits zu symbolisieren, dass es sich um Start- und Ende-Tag in einem handelt, insbesondere aber, um [XHTML](https://de.wikipedia.org/wiki/Extensible_Hypertext_Markup_Language)-konform zu sein, geben wir für solche stand-alone Tags den Slash vor der schließenden spitzen Klammer an, d.h. wir schreiben `<br />`.

## Grundgerüst einer HTML-Seite

Prinzipiell besteht eine HTML-Seite aus einem `<head>`- und einem `<body>`-Bereich. Im <head>-Bereich können Metadaten über die Seite definiert werden. Der `<body>`-Bereich definiert den sichtbaren Bereich der Seite, also das, was im Browser dargestellt wird. Eingeschlossen werden der `<head>`- und der `<body>`-Bereich von einem `<html>`-Element.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Seitentitel</title>
  </head>
  <body>
    <h1>Das ist eine große Überschrift</h1>
    <p>Das ist ein Absatz.</p>
  </body>
</html>
```


Das obige Beispiel zeigt ein Grundgerüst einer HTML-Seite. `<!DOCTYPE html>` gibt dem Browser an, dass es sich um eine HTML-Datei handelt, die vom Browser **"gerendert"**, d.h. dargestellt wird.

Der `<head>`-Bereich enthält in diesem Beispiel nur ein `<title>`-Element. Dieser Titel wird im Browser im Reiter (Tab) gezeigt. Außerdem wird der Titel in der Ergebnisliste einer Suchmaschine verwendet.

Das `<body>`-Element, also der im Browser dargestellte Bereich, enthält eine Überschrift (`<h1>`) und einen Absatz (`<p>`).

!!! question "Aufgabe:"
    Erstellen Sie eine Datei ```index.html``` und fügen Sie obigen HTML-Code ein. Rufen Sie die Datei im Browser auf.


## Block- und Inline-Elemente

Generell wird zwischen zwei Arten von HTML-Elementen unterschieden:

- Blockelemente
- Inline-Elemente

**Blockelemente** verwenden die gesamte Breite der Browseransicht (des sogenannten **Viewports**). Das bedeutet, dass ein Blockelement stets in einer neuen Zeile beginnt und neben einem Blockelement kein weiteres Element ist (sondern in einer neuen Zeile beginnt).

**Inline-Elemente** nehmen genau so viel Breite ein, wie nötig (Breite des Inhalts) und beginnen nicht in einer neuen Zeile und enden auch nicht mit einem Zeilenumbruch.

Beispiele für Inline- und Blockelemente (Reiter "Result" wählen, um Ergebnis zu sehen):

<iframe width="100%" height="300" src="//jsfiddle.net/jfreiheit/fze5kd0L/4/embedded/html,css,result/" allowfullscreen="allowfullscreen" allowpaymentrequest="" frameborder="0"></iframe>

Eine Übersicht über alle HTML-Elemente mit Erläuterungen findet sich hier.

!!! question "Aufgabe:"
    Erweitern Sie Ihre Datei ```index.html``` und fügen Sie mindestens folgende Elemente ein:

    - 2 verschiedene Überschriften (`h1`, ..., `h6`)
    - eine nummerierte Liste (ordered list - `ol`) mit 3 Einträgen (list items - `li`)
    - eine Strichpunktliste (unordered list - `ul`) mit 3 Einträgen (`li`)
    - eine Tabelle (`table`); diese besteht aus einem Tabellenkopf (table head - `thead`) und einem Tabellenkörper (table body - `tbody`)
      - der thead enthält eine Zeile (table row - `tr`) als Tabellenüberschrift, wobei jede einzelne Überschrift (eine Spalte) als `th` definiert wird
      - der tbody enthält mehrere Zeilen (`tr`); jede Zeile enthält so viele Dateneinträge (table data - `td`) wie es Spalten gibt
    - einen Hyperlink (anchor - `a`), der ein Verweis auf die HTW-Seite enthält
    - ein Bild (image - `img`)

    Rufen Sie die Datei im Browser auf.

## Attribute

## Weitere Informationen über HTML

- [Folien HTML](./files/01_WT_HTML.pdf)
