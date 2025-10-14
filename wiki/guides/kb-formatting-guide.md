---
source-git-commit: c587986edc925c49bf95ab935888b59f265371af
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---
# Handbuch zur KB-Formatierung

## Autor in Markdown

Im Allgemeinen verwenden wir das Stilhandbuch zur [Adobe Experience League Markdown-Syntax](https://experienceleague.adobe.com/docs/authoring-guide-exl/using/markdown/syntax-style-guide.html?lang=de) es gibt jedoch einige Unterschiede und Ausnahmen. Außerdem sind in bestimmten Fällen bestimmte HTML-Tags erforderlich.

Im Folgenden finden Sie Beispiele für die Markdown-Formatierung, die am häufigsten in unserem Repository verwendet wird.

## Grundlegende Formatierung

Um Text fett zu formatieren, setzen Sie ihn in zwei Sternchen ein:

`This will be **bold** text`

Um Text kursiv zu formatieren, verwenden Sie ein einzelnes Sternchen:

`This text will be *italics*`

Um Text wie unterstrichen zu formatieren, verwenden Sie das `<ins>`-Tag:

`<ins>This text will be underlined</ins>`

Um einen Zeilenumbruch hinzuzufügen, verwenden Sie das Tag `<br>` HTML .


## Kopfzeilen

Verwenden Sie die folgende Formatierung für Kopfzeilen von H2 bis H5. H1 wird nie verwendet, da der Artikeltitel als H1 gilt.

`## Header 2 `

`### Header 3 `

`#### Header 4`

`##### Header 5`

## Inline-Code und -Blöcke

Schließen Sie das Codeelement, das Sie hervorheben möchten, mit einzelnen Backticks ein:

Dies ist \`inline code\` innerhalb eines Textabsatzes.

### Code-Blöcke

Um einen Code-Block einzufügen, schließen Sie den Code-Block in drei Backticks ein und geben Sie die Sprache nach dem Öffnen von drei Backticks an:

\`\`\` SQL

WÄHLEN SIE TABLE_NAME ALS `Table`,
ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WOBEI TABLE_SCHEMA = &quot;%PROJECT_ID%&quot;
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;

\`\`\`

Dies wird wie folgt dargestellt:

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "%project_id%"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

Gemäß unseren Verknüpfungsregeln müssen Sie immer eine Sprache für den Code-Block angeben.

Eine Liste der unterstützten Sprachen finden Sie unter https://github.com/github/linguist/blob/master/lib/linguist/languages.yml.

Wenn die Hervorhebung in Markdown für eine bestimmte Sprache nicht funktioniert (d. h., die Sprache wird nicht unterstützt), verwenden Sie die folgende HTML, um sie bei der Veröffentlichung auf https://support.magento.com/hc/en-us/ zumindest hervorzuheben:

```html
<pre><code class="language-%language-code%"
your code here
</pre></code>
```

``%language-code%`` sind die von [Prism.js unterstützten Sprachen](https://prismjs.com/#supported-languages) definierten Codes.

## Listen

Listen werden immer durch leere Zeilen vom Rest des Inhalts getrennt. Listen sollten eine Leerzeile vorangestellt und von dieser gefolgt werden.

Verwenden Sie die folgende Formatierung für sortierte Listen:

```markdown
1. First numbered list item.
1. Second numbered list item.
...
1. Last numbered list item.
```

Um eine ungeordnete Aufzählungsliste zu erstellen, beginnen Sie eine Zeile mit *, oder +, oder -. Wählen Sie jedoch eine Methode aus und verwenden Sie sie konsistent im gesamten Artikel.

Beispiel:

```markdown
* Unordered list item.
* Unordered list item.
---
* Last unordered list item.
```

Um Inhalt zwischen Listenelementen hinzuzufügen, fügen Sie vier Leerzeichen am Anfang der Zeile hinzu:

```markdown
* List item.
* List item.
    Here's some content between list items.
* Here we continue the list
```

Sie können Listen auch auf diese Weise einbetten.

## Relationen

Externe Links sind unkompliziert:

```markdown
[Adobe](https://www.adobe.com)
```

### Links zu Anlagen

Jede Art von Anhang sollte die Formate .png, .jpg und .jpeg aufweisen. Aus Sicherheitsgründen akzeptieren wir nur Anhänge, die in einem der drei Formate vorliegen.

Um ein Bild einzufügen, platzieren Sie das Bild in *Assets*-Unterordner im selben Abschnittsordner wie den Artikel und verwenden Sie die folgende Syntax, um das Bild in Ihren Artikel einzufügen:

```markdown
![alt text](assets/image.png)
```

Wenn Sie die Bildgröße anpassen möchten, müssen Sie dazu das folgende HTML-Tag verwenden:

```html
<img src = "assets/image.png" alt = "your alt text" width="custom width, ex: 250px">
```

```markdown
[asset_title](assets/%file_name%).
```

### Links zu bestimmten Abschnitten des Artikels

Wenn Sie einen Abschnitt innerhalb Ihres Artikels referenzieren müssen, müssen Sie keinen separaten Anker erstellen. Sie werden zur Veröffentlichungszeit automatisch für alle H2-H6-Überschriften generiert. Die Referenzzeichen werden aus dem -Header generiert, indem alle Wörter klein geschrieben werden und &quot;-&quot; zum Trennen der Wörter verwendet wird.

Beispiel:

```markdown
## This is header
```

Dies ist ein Link zu dieser Kopfzeile:

```markdown
[this is link to the anchor in the same article](#this-is-header)
```

Wenn Sie auf ein anderes Element als die Kopfzeile verweisen müssen, definieren Sie mithilfe von HTML das hinzuzufügende Element und verwenden [id](https://www.w3schools.com/html/html_id.asp). Sie können dann Markdown oder HTML verwenden, um auf diese ID zu verweisen.

### Relative Links und Links zu anderen Artikeln

Verwenden Sie keine relativen Links, um auf unsere Artikel in der Support-Wissensdatenbank zu verweisen. Diese Links funktionieren nicht, wenn Ihr Artikel im [Adobe Commerce-Hilfezentrum veröffentlicht &#x200B;](https://support.magento.com/hc/en-us).
Verwenden Sie vollständige Hyperlinks aus dem [Adobe Commerce-Hilfezentrum](https://support.magento.com/hc/en-us).


## Tabellen

Verwenden Sie [HTML-Formatierung für Tabellen](https://www.w3schools.com/html/html_tables.asp).


## Warnungen und Informationsblöcke

Block mit Erfolgsnotizen:

```
>![success]
>
>This is a success note
```

Warnblock:

```
>![warning]
>
>This is a warning
```

Informationsnotizblock:

```
>![info]
>
>This is a block with additional info
```
