---
title: "MDVA-40120: Sortieren des GraphQL-Produkts DESC/ASC funktioniert nicht"
description: Der Patch MDVA-40120 behebt das Problem, dass die GraphQL-Sortierung nach DESC/ASC nicht mit Produkten mit derselben Relevanz oder demselben Preis funktioniert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-40120. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: f04373d6-d3e8-47ba-9261-87fad8dff327
feature: GraphQL, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# MDVA-40120: Sortieren von GraphQL-Produkt DESC/ASC funktioniert nicht

Der Patch MDVA-40120 behebt das Problem, dass die GraphQL-Sortierung nach DESC/ASC nicht mit Produkten mit derselben Relevanz oder demselben Preis funktioniert. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-40120. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Voraussetzungen</u>:

Erstellen Sie einige verschiedene Produkte mit demselben Preis.

<u>Zu reproduzierende Schritte</u>:

1. Führen Sie die folgende GraphQL-Abfrage aus:
   <pre>
    <code class="language-graphql">
    {
      products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: ASC}) {
        total_count
        items {
          name
          sku
        }
      }
    }
    </code>
    </pre>
1. Überprüfen Sie die Antwort.
1. Sortierreihenfolge ändern von **ASC** nach **DESC** in der GraphQL-Abfrage:
   <pre>
    <code class="language-graphql">
    {
      products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: DESC}) {
        total_count
        items {
          name
          sku
        }
      }
    }
    </code>
    </pre>
1. Überprüfen Sie die Antwort.

<u>Erwartete Ergebnisse</u>:

Die Produktliste in der GraphQL-Antwort sollte entsprechend der Sortierreihenfolge geändert werden.

<u>Tatsächliche Ergebnisse</u>:

Die Sortierreihenfolge bleibt unverändert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
