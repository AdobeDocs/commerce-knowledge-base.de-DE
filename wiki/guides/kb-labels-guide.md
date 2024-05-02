---
source-git-commit: 88a2b8fe11d718f33c26bbc6f407c55d9f1fd189
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---
# Anleitung für KB-Beschriftungen

Dieses Dokument enthält Richtlinien zum Hinzufügen von Bezeichnungen zu Artikeln in der Knowledge Base des Adobe Commerce-Supports.
Beschriftungen (auch als Tags bezeichnet) verbessern das Sucherlebnis in der [Wissensdatenbank zur Adobe Commerce-Unterstützung](https://support.magento.com/hc/en-us).
Beschriftungen werden im Feld &quot;Beschriftungen&quot;im Metadatenabschnitt einer Artikeldatei hinzugefügt, durch Kommas getrennt, kein Leerzeichen zwischen einem Komma und der nächsten Beschriftung.
Siehe [../../.github/CONTRIBUTING.md#metadata] für Details.

## Allgemeine Bestimmungen

Fügen Sie für jeden Artikel die folgenden Beschriftungstypen hinzu:

* Beschriftung(n) für das/die Produkt(e). (erforderlich)
* Beschriftungen für betroffene Versionen. (erforderlich, mit Ausnahme von Artikeln, die sich auf allgemeine Unterstützung beziehen)
* Beschriftung für den Inhaltstyp. (erforderlich)
* Beschriftungen für wichtige technische Komponenten.(falls zutreffend)
* Beschriftungen für Prozesse/Funktionen, bei denen eine Fehlerbehebung durchgeführt/beschrieben wird. (falls zutreffend)
* Beschriftungen für das Problem, das behoben/beschrieben wird. (falls zutreffend)

In den folgenden Abschnitten finden Sie ausführliche Empfehlungen zum Definieren von Bezeichnungen für die einzelnen Bezeichnungstypen.

## Beschriftungen für Produkte

<table>
<tbody>
  <tr>
    <th>Produktname</th>
    <th>Titel</th>
  </tr>
  <tr>
    <td>Adobe Commerce (alle Bereitstellungsmethoden) </td>
    <td>
    "Adobe Commerce,Cloud-Infrastruktur,On-Premise"
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce auf Cloud-Infrastruktur</td>
    <td>
      "Adobe Commerce,Cloud-Infrastruktur"
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce vor Ort</td>
    <td>"Adobe Commerce, vor Ort"</td>
  </tr>
  <tr>
    <td>Magento Business Intelligence (MBI)</td>
    <td>
        "Magento Business Intelligence,MBI"
    </td>
  </tr>
   <tr>
    <td>Magento Open Source</td>
    <td>
        "Magento Open Source"
    </td>
  </tr>
  <tr>
    <td>B2B für Adobe Commerce</td>
    <td>"B2B"</td>
  </tr>
  <tr>
    <td>PWA für Adobe Commerce</td>
    <td>"PWA"</td>
  </tr>
  <tr>
    <td>Venia-Storefront-Projekt</td>
    <td>"Venia"</td>
  </tr>
  <tr>
    <td>Quality Patches Tool, QPT</td>
    <td>"Quality Patches Tool,QPT Patches"</td>
  </tr>
  </tbody>
</table>

## Beschriftungen für Produktversionen

* Fügen Sie für jede Version von Adobe Commerce eine separate Bezeichnung hinzu. Beispiel: &quot;2.3.7&quot;
* Fügen Sie keine Bezeichnungen für Intervalle hinzu.
Das heißt, wenn 2.3.0-2.3.5 betroffen ist, wird Folgendes hinzugefügt: &quot;2.3.0,2.3.1,2.3.2,2.3.2-p2,2.3.3,2.3.3-p1,2.3.4,2.3.4-p2,2.3.5-p1,2.3.5-p2&quot; NICHT &quot;2.2 3.0-2.3.5&quot;
* Fügen Sie keine Bezeichnungen mit .x hinzu. Beispiel: &quot;2.3.x&quot;

## Beschriftungen für den Inhaltstyp (basierend auf der Kategorie)

<table>
  <tbody>
    <tr>
      <th>Kategorie</th>
      <th>Titel</th>
    </tr>
    <tr>
      <td>Best Practices</td>
      <td>"Best Practices"(nicht "Best Practice"oder "Best Practice")</td>
    </tr>
    <tr>
      <td>
        Fehlerbehebung
      </td>
      <td>
      "Fehlerbehebung"
      </td>
    </tr>
    <tr>
      <td>Anleitung</td>
      <td>"How to"</td>
    </tr>
    <tr>
      <td>FAQs</td>
      <td >"FAQs"</td>
    </tr>
  </tbody>
</table>

## Beschriftungen für wichtige technische Komponenten

* Verwenden Sie die Groß-/Kleinschreibung gemäß der offiziellen Komponentenbenennung.
* Verwenden Sie keine Synonyme, eine Bezeichnung für eine Komponente.
* Eine Wortbeschriftung ist vorzuziehen. Wenn der Komponentenname jedoch mehrere Wörter enthält, verwenden Sie mehrere Wörter. Fügen Sie keine Problembeschreibungen hinzu. Das heißt, setzen Sie &quot;Elasticsearch&quot;anstelle von &quot;Elasticsearch-Probleme&quot;.
* Wenn der Inhalt nur für eine bestimmte Version der Komponente relevant ist, fügen Sie eine Beschriftung mit Name und Version hinzu.\
  Beispiel: &quot;Elasticsearch 5&quot;. Wenn es für mehrere Versionen relevant ist, fügen Sie mehrere Beschriftungen dieses Typs hinzu. Beispiel: &quot;Elasticsearch 5&quot;, &quot;Elasticsearch 6&quot;. Verwenden Sie gegebenenfalls &quot;x&quot;für mehrere Versionen. Beispiel: &quot;Elasticsearch 2.x&quot;

Beispiele:

* &quot;Elasticsearch&quot;
* &quot;New Relic&quot;
* &quot;Web-Setup-Assistent&quot;

## Beschriftungen für Prozess/Funktionalität, die behoben/beschrieben werden

* Verwenden Sie niedrige Groß-/Kleinschreibung, mit Ausnahme von Eigennamen.
* Verwenden Sie keine Synonyme, sondern eine Bezeichnung für eine Entität.
* Eine Wortbezeichnung ist vorzuziehen. Fügen Sie keine Problembeschreibung hinzu. Setzen Sie also &quot;Datenbank&quot;anstelle von &quot;Datenbankabstürzen&quot;.

Beispiele: 

* &quot;database&quot;
* &quot;cron&quot;
* &quot;deployment&quot;
* &quot;gebündelte Aktualisierung&quot;

## Beschriftungen für das Problem, das behoben/beschrieben wird

* Verwenden Sie niedrige Groß-/Kleinschreibung, mit Ausnahme von Eigennamen.
* Verwenden Sie keine Synonyme, sondern eine Bezeichnung für eine Entität.
* Eine Wortbezeichnung ist vorzuziehen. Konvertieren Sie keine Fehlermeldung in eine Beschriftung.

Beispiele:

* &quot;site down&quot;
* &quot;500 error&quot;
* &quot;hängengebliebene Krone&quot;
