<a id="style-guide-for-powershell-docs" class="xliff"></a>
# Styleguide für PowerShell-Dokumente


<a id="titlesheadings" class="xliff"></a>
## Titel/Überschriften

* Titel/Überschriften (alles, dem \# vorangestellt ist) müssen mit einem Zeilenumbruch ausgeführt werden
* Nur der erste Buchstaben des Titels und alle Eigennamen im Titel sollten groß geschrieben werden
* Nur 1 H1 pro Dokument
* Wenn Sie Referenzinhalte bearbeiten, werden die H2s von platyPS vorgeschriebenen und sollten nicht hinzugefügt oder entfernt werden, da dies zu einer Buildunterbrechung führt
* Verwenden Sie nur \#-Stilheader (im Gegensatz zum „=“ oder dem Stilheader \-)

<a id="correct" class="xliff"></a>
### Richtig

```
# Header 1

## Header 2

### Header 3

```

<a id="incorrect" class="xliff"></a>
### Falsch

```
Header 1
========

Header 2
--------

### Header 3
```

<a id="syntax" class="xliff"></a>
## Syntax

* Verwenden Sie \` bei der Kommunikation über ein Cmdlet im Absatz, um Cmdlet-Namen zu markieren
  * Richtiges Beispiel: Dieses `Write-Host`-Cmdlet ermöglicht es...
  * Falsches Beispiel: Dieses **Write-Host**-Cmdlet kann... und wird per Pipeline übertragen an das out-file-Cmdlet...
* Beim Schreiben eines Artikels (im Gegensatz zu Referenzinhalt) sollte die erste Instanz eines Cmdlet-Namens ein Link zur Cmdlet-Dokumentation sein
* Alle Blöcke der PowerShell-Syntax sollten &#96;&#96;&#96;powershell verwenden
* Starten Sie PowerShell-Befehle nicht mit „`PS C:\>`“
  * Richtiges Beispiel:
  ```powershell
  Get-Process
  ```
  * Falsches Beispiel:
  ```powershell
  PS C:\> Get-Process
  ```
* Ausgabe, die von PowerShell-Befehlen ausgegeben wurde, sollte kommentiert werden, um sie am Empfangen von Syntaxhervorhebung zu hindern
* Eigenschaftsnamen und Parameternamen sollten **fett** geschrieben werden
* PowerShell-Cmdlets haben die [Pascal-Schreibweise](https://en.wikipedia.org/wiki/PascalCase). Verben sind durch einen Bindestrich von Substantiven getrennt.

<a id="lists" class="xliff"></a>
## Listen

* Beenden Sie Listenelemente nicht mit einem Punkt (sofern sie nicht mehrere Sätze enthalten)
* Wenn Ihre Liste mehrere Sätze enthält, erwägen Sie die Verwendung eines Header 3/4/5 (falls zutreffend) unter Ihrer primären Idee

<a id="links" class="xliff"></a>
## Links

* Links werden immer mit MarkDown-Syntax `[friendlyname](url)` gekennzeichnet
* Links sollten einen Anzeigenamen haben, falls zutreffend, am besten den Titel der verknüpften Seite
  * **Ausnahme**: Links zu Seiten, die nicht von Microsoft stammen, sollten nur eine URL enthalten
* Alle Elemente im Abschnitt „Verwandte Links“ am unteren Rand sollten mit einem Link versehen sein. 

<a id="line-breaks" class="xliff"></a>
## Zeilenumbrüche

* Sie müssen semantische Zeilenumbrüche einschließen
* Sie sollten Zeilen auf 100 Zeichen einschränken (Element öffnen: Tools helfen uns dies zu überprüfen).
* Sie können zusätzliche Zeilenumbrüche für PS4+ entfernen, aber NICHT für ps3 (Überprüfung erforderlich)
