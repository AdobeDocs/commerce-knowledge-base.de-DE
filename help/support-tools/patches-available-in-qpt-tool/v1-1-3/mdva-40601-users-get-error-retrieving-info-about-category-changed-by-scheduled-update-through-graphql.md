---
title: "MDVA-40601: Daten zur Kategorie, die durch geplante Aktualisierung über GraphQL geändert wurde, können nicht abgerufen werden."
description: Der MDVA-40601 Adobe Commerce-Qualitäts-Patch behebt das Problem, dass Benutzer einen Fehler erhalten, wenn sie Informationen über Kategorien erhalten, die durch geplante Aktualisierungen über GraphQL geändert wurden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.3 installiert ist. Die Patch-ID lautet MDVA-40601. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: b1ea93e7-8d4a-4bdd-8267-cc60de25bd39
feature: Categories, GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-40601: Es können keine Daten zu einer Kategorie abgerufen werden, die durch eine geplante Aktualisierung über GraphQL geändert wurde.

Der MDVA-40601 Adobe Commerce-Qualitäts-Patch behebt das Problem, dass Benutzer einen Fehler erhalten, wenn sie Informationen über Kategorien erhalten, die durch geplante Aktualisierungen über GraphQL geändert wurden. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.3 installiert ist. Die Patch-ID lautet MDVA-40601. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3 und 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzer erhalten eine Fehlermeldung, wenn sie versuchen, Informationen über Kategorien abzurufen, die durch geplante Aktualisierungen über GraphQL geändert wurden.

<u>Zu reproduzierende Schritte</u>:

1. Richten Sie eine Kategoriestruktur mit einer Unterkategorie wie unten gezeigt ein:

   <pre>
   <code class="language-graphql">
   - Root
    - Some category
         - Some child category
   </code>
   </pre>

1. Führen Sie die GraphQL-Abfrage mit der Kennung &quot;Beliebige Kategorie&quot;49 aus.

   <pre>
    <code class="language-graphql">
    query {
     category(id: 49) {
      name
      children {
        name
       }
     }
   }
   </code>
   </pre>

   Ergebnis:

   <pre>
    <code class="language-graphql">
    {
      "data": {
        "category": {
          "name": "Some category",
          "children": [
            {
              "name": "Some child category"
            }
          ]
        }
      }
    }
    </code>
    </pre>

1. Erstellen Sie ein Planupdate für &quot;Some Category&quot;mit einem anderen Kategorienamen.
1. Warten Sie, bis die Aktualisierung des Zeitplans aktiviert wurde.
1. Führen Sie dieselbe Abfrage wie oben beschrieben aus.

<u>Erwartete Ergebnisse</u>:

Sie erhalten dasselbe Ergebnis, jedoch mit dem aktualisierten Kategorienamen.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten den folgenden Fehler:

<pre>
<code class="language-graphql">
{
  "errors": [
    {
      "debugMessage": "uasort() expects parameter 1 to be array, string given",
      "message": "Internal server error",
      "extensions": {
        "category": "internal"
      },
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "category"
      ]
    }
  ],
  "data": {
    "category": null
  }
}
</code>
</pre>

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungstyp die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu Qualitäts-Patches für Adobe Commerce finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
