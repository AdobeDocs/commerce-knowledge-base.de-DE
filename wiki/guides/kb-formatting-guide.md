---
source-git-commit: c587986edc925c49bf95ab935888b59f265371af
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---
# KB-Formatierungsanleitung

## Autor in Markdown

Im Allgemeinen verwenden wir [Adobe Experience League Markdown-Syntaxhandbuch](https://experienceleague.adobe.com/docs/authoring-guide-exl/using/markdown/syntax-style-guide.html?lang=en), aber es gibt einige Unterschiede und Ausnahmen. Außerdem sind bestimmte HTML-Tags in bestimmten Fällen erforderlich.

Im Folgenden finden Sie Beispiele für die Markdown-Formatierung, die am häufigsten in unserem Repo verwendet wird.

## Grundlegende Formatierung

Um Text fett zu formatieren, fügen Sie ihn in zwei Sternchen ein:

`This will be **bold** text`

Um Text kursiv zu formatieren, verwenden Sie ein einzelnes Sternchen:

`This text will be *italics*`

Um Text wie unterstrichen zu formatieren, verwenden Sie die `<ins>` Tag:

`<ins>This text will be underlined</ins>`

Verwenden Sie zum Hinzufügen eines Zeilenumbruchs die `<br>` HTML-Tag.


## Kopfzeilen

Verwenden Sie die folgende Formatierung für Kopfzeilen von H2 bis H5. H1 wird nie verwendet, da der Artikeltitel als H1 gilt.

`## Header 2 `

`### Header 3 `

`#### Header 4`

`##### Header 5`

## Inline-Code und Blöcke

Verwenden Sie einzelne Backticks, um das Codeelement einzuschließen, das Sie hervorheben möchten:

Dies ist \&quot;Inline-Code\&quot; in einem Textabsatz.

### Codeblöcke

Um einen Codeblock einzufügen, fügen Sie den Codeblock in drei Backticks ein und geben Sie die Sprache nach dem Öffnen von drei Backticks an:

\`\`\` sql

SELECT TABLE_NAME AS `Table`, ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
VON information_schema.TABLES WHERE TABLE_SCHEMA = &quot;%project_id%&quot; ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;

\`\`\`

Dies wird wie folgt dargestellt:

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "%project_id%"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

Gemäß unseren Linking-Regeln müssen Sie immer eine Sprache für den Codeblock angeben.

Eine Liste der unterstützten Sprachen finden Sie unter https://github.com/github/linguist/blob/master/lib/linguist/languages.yml.

Wenn die Hervorhebung für eine bestimmte Sprache in Markdown nicht funktioniert (d. h. die Sprache wird nicht unterstützt), verwenden Sie folgende HTML, um sie mindestens bei der Veröffentlichung unter https://support.magento.com/hc/en-us/ hervorgehoben zu machen:

```html
<pre><code class="language-%language-code%"
your code here
</pre></code>
```

Wo ``%language-code%`` sind die von [Unterstützte Sprachen für Prism.js](https://prismjs.com/#supported-languages).

## Listen

Trennen Sie Listen immer vom Rest des Inhalts durch leere Zeilen. Der Liste sollte eine leere Zeile vorangestellt werden.

Verwenden Sie die folgende Formatierung für sortierte Listen:

```markdown
1. First numbered list item.
1. Second numbered list item.
...
1. Last numbered list item.
```

Um eine ungeordnete Liste mit Aufzählungszeichen zu erstellen, beginnen Sie eine Zeile mit *, oder + oder -. Wählen Sie jedoch eine Methode aus und verwenden Sie sie durchgängig im gesamten Artikel.

Beispiel:

```markdown
* Unordered list item.
* Unordered list item.
---
* Last unordered list item.
```

Um Inhalte zwischen Listenelementen hinzuzufügen, fügen Sie am Anfang der Zeile vier Leerzeichen hinzu:

```markdown
* List item.
* List item.
    Here's some content between list items.
* Here we continue the list
```

Sie können Listen auch auf diese Weise einbetten.

## Links

Externe Links sind einfach:

```markdown
[Adobe](https://www.adobe.com)
```

### Links zu Anlagen

Jede Art von Anlage sollte in den Formaten .png, .jpg und .jpeg vorliegen. Aus Sicherheitsgründen akzeptieren wir nur Anhänge, die in einem der drei Formate enthalten sind.

Um ein Bild einzufügen, platzieren Sie das Bild auf *Assets* Unterordner im selben Abschnittsordner wie der Artikel und verwenden Sie die folgende Syntax, um das Bild in Ihren Artikel einzufügen:

```markdown
![alt text](assets/image.png)
```

Wenn Sie die Bildgröße anpassen möchten, müssen Sie dies mit dem folgenden HTML-Tag tun:

```html
<img src = "assets/image.png" alt = "your alt text" width="custom width, ex: 250px">
```

```markdown
[asset_title](assets/%file_name%).
```

### Links zu bestimmten Abschnitten im Artikel

Wenn Sie einen Abschnitt in Ihrem Artikel referenzieren müssen, müssen Sie keinen separaten Anker erstellen. Sie werden automatisch zum Zeitpunkt der Veröffentlichung für alle H2-H6-Überschriften generiert. Die Anker werden aus der Kopfzeile generiert, indem sie alle Wörter in Kleinbuchstaben schreiben und &quot;-&quot;zur Trennung von Wörtern verwenden.

Beispiel:

```markdown
## This is header
```

Dies ist ein Link zu dieser Kopfzeile:

```markdown
[this is link to the anchor in the same article](#this-is-header)
```

Wenn Sie auf ein anderes Element als die Kopfzeile verweisen müssen, verwenden Sie HTML, um das hinzuzufügende Element zu definieren. Verwenden Sie dazu die [id-Attribut](https://www.w3schools.com/html/html_id.asp). Sie können dann Markdown oder HTML verwenden, um auf diese ID zu verweisen.

### Relative Links und Links zu anderen Artikeln

Verwenden Sie keine relativen Links, um auf unsere Support-Knowledge Base-Artikel zu verweisen. Diese Links funktionieren nicht, wenn Ihr Artikel in der [Adobe Commerce Help Center](https://support.magento.com/hc/en-us).
Bitte verwenden Sie vollständige Hyperlinks aus dem [Adobe Commerce Help Center](https://support.magento.com/hc/en-us).


## Tabellen

Verwendung [Tabellenformatierung](https://www.w3schools.com/html/html_tables.asp).


## Warnungen und Informationsblöcke

Block der Erfolgserfassung:

```
>![success]
>
>This is a success note
```

Warnungsblock:

```
>![warning]
>
>This is a warning
```

Info-Hinweisblock:

```
>![info]
>
>This is a block with additional info
```
