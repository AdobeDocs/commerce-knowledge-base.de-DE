---
source-git-commit: 88a2b8fe11d718f33c26bbc6f407c55d9f1fd189
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---
# Handbuch zu KB-Kennzeichnungen

Dieses Dokument enthält Richtlinien zum Hinzufügen von Beschriftungen zu Artikeln in der Adobe Commerce-Support-Wissensdatenbank.
Beschriftungen (auch als Tags bezeichnet) verbessern das Sucherlebnis in der Wissensdatenbank zum [Adobe Commerce-Support](https://support.magento.com/hc/en-us).
Kennzeichnungen werden im Feld „Kennzeichnungen“ im Metadatenabschnitt einer Artikeldatei hinzugefügt, durch Kommas getrennt, kein Leerzeichen zwischen einem Komma und der nächsten Kennzeichnung.
github/CONTRIBUTING.md Weitere Informationen finden Sie unter [../../.#metadata].

## Allgemeine Bestimmungen

Fügen Sie für jeden Artikel die folgenden Titeltypen hinzu:

* Etikett(e) für Produkt(e). (erforderlich)
* Titel der betroffenen Versionen. (Erforderlich, mit Ausnahme von Artikeln, die sich auf den allgemeinen Support beziehen)
* Titel für Inhaltstyp. (erforderlich)
* Beschriftungen für wichtige technische Komponenten.(falls zutreffend)
* Kennzeichnungen für Prozesse/Funktionen, bei denen eine Fehlerbehebung durchgeführt/beschrieben wird. (falls zutreffend)
* Kennzeichnungen für das zu behebende/beschriebene Problem. (falls zutreffend)

In den folgenden Abschnitten finden Sie detaillierte Empfehlungen zum Definieren von Kennzeichnungen für jeden dieser Kennzeichnungstypen.

## Kennzeichnungen für Produkte

<table>
<tbody>
  <tr>
    <th>Produktname</th>
    <th>Bezeichnung</th>
  </tr>
  <tr>
    <td>Adobe Commerce (alle Bereitstellungsmethoden) </td>
    <td>
    "Adobe Commerce,Cloud-Infrastruktur,On-Premise“
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce auf Cloud-Infrastruktur</td>
    <td>
      "Adobe Commerce, Cloud-Infrastruktur“
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce On-Premises</td>
    <td>"Adobe Commerce, On-Premises“</td>
  </tr>
  <tr>
    <td>Magento Business Intelligence (MBI)</td>
    <td>
        "Magento Business Intelligence,MBI“
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
    <td>„B2B“</td>
  </tr>
  <tr>
    <td>PWA für Adobe Commerce</td>
    <td>"PWA"</td>
  </tr>
  <tr>
    <td>Venia-Storefront-Projekt</td>
    <td>Venia</td>
  </tr>
  <tr>
    <td>Quality Patches Tool, QPT</td>
    <td>„Quality Patches Tool, QPT Patches“</td>
  </tr>
  </tbody>
</table>

## Beschriftungen für Produktversionen

* Fügen Sie für jede Version von Adobe Commerce einen separaten Titel hinzu. Beispiel: „2.3.7“
* Keine Beschriftungen für Intervalle hinzufügen.
Wenn 2.3.0-2.3.5 betroffen sind, fügen Sie hinzu: „2.3.0,2.3.1,2.3.2,2.3.2-p2,2.3.3,2.3.3-p1,2.3.4,2.3.4-p2,2.3.5-p1,2.3.5-p2“
NICHT 2.3.0-2.3.5
* Keine Bezeichnungen mit .x hinzufügen. Beispiel: „2.3.x“

## Kennzeichnungen für den Inhaltstyp (basierend auf der Kategorie)

<table>
  <tbody>
    <tr>
      <th>Kategorie</th>
      <th>Bezeichnung</th>
    </tr>
    <tr>
      <td>Best Practices</td>
      <td>„Best Practices“ (nicht „Best Practices“ oder „Best Practices„)</td>
    </tr>
    <tr>
      <td>
        Fehlerbehebung
      </td>
      <td>
      „Fehlerbehebung“
      </td>
    </tr>
    <tr>
      <td>Anleitung</td>
      <td>„Anleitung“</td>
    </tr>
    <tr>
      <td>FAQs</td>
      <td >„FAQs“</td>
    </tr>
  </tbody>
</table>

## Beschriftungen für wichtige technische Komponenten

* Verwenden Sie die Groß-/Kleinschreibung gemäß der offiziellen Benennung der Komponente.
* Verwenden Sie keine Synonyme, sondern nur eine Bezeichnung für eine Komponente.
* Beschriftungen mit einem Wort sind vorzuziehen. Wenn der Komponentenname jedoch mehrere Wörter enthält, verwenden Sie mehrere Wörter. Keine Problembeschreibungen hinzufügen. Das heißt, stellen Sie &quot;Elasticsearch&quot; statt &quot;Elasticsearch Probleme“.
* Wenn der Inhalt nur für eine bestimmte Version der Komponente relevant ist, fügen Sie eine Bezeichnung hinzu, die Name + Version enthält.\
  Beispiel: &quot;Elasticsearch 5“. Wenn es für mehrere bestimmte Versionen relevant ist, fügen Sie mehrere Bezeichnungen dieses Typs hinzu. Beispiel: &quot;Elasticsearch 5“, &quot;Elasticsearch 6“. Verwenden Sie gegebenenfalls „x“ für mehrere Versionen. Beispiel: &quot;Elasticsearch 2.x“

Beispiele:

* &quot;Elasticsearch&quot;
* &quot;New Relic
* „Websetup-Assistent“

## Kennzeichnungen für Prozesse/Funktionen, bei denen eine Fehlerbehebung durchgeführt/beschrieben wird

* Verwenden Sie Kleinbuchstaben, mit Ausnahme von Eigennamen.
* Verwenden Sie keine Synonyme, nur eine Bezeichnung für eine Entität.
* Eine Wortbezeichnung ist vorzuziehen. Keine Problembeschreibung hinzufügen. Das heißt, setzen Sie „Datenbank“ anstelle von „Datenbank-Abstürze“.

Beispiele: 

* „Datenbank“
* „Cron“
* „Bereitstellung“
* „Massenaktualisierung“

## Kennzeichnungen für das zu behebende/beschriebene Problem

* Verwenden Sie Kleinbuchstaben, mit Ausnahme von Eigennamen.
* Verwenden Sie keine Synonyme, nur eine Bezeichnung für eine Entität.
* Eine Wortbezeichnung ist vorzuziehen. Konvertieren Sie keine Fehlermeldung in eine Bezeichnung.

Beispiele:

* „Site Down“
* „500-Fehler“
* „stecken geblieben“
