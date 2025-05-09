---
title: 'MDVA-40120: GraphQL-Produkt DESC/ASC-Sortierung funktioniert nicht'
description: Der Patch MDVA-40120 löst das Problem, dass die Sortierung von GraphQL nach DESC/ASC bei Produkten mit gleicher Relevanz oder demselben Preis nicht funktioniert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-40120. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
exl-id: f04373d6-d3e8-47ba-9261-87fad8dff327
feature: GraphQL, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# MDVA-40120: GraphQL-Produkt DESC/ASC-Sortierung funktioniert nicht

Der Patch MDVA-40120 löst das Problem, dass die Sortierung von GraphQL nach DESC/ASC bei Produkten mit gleicher Relevanz oder demselben Preis nicht funktioniert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-40120. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

<u>Voraussetzungen</u>:

Erstellen Sie einige verschiedene Produkte mit dem gleichen Preis.

<u>Schritte zur Reproduktion</u>:

1. Führen Sie die folgende GraphQL-Abfrage aus:
   <pre>
    <code class="language-graphql">
    &lbrace;
      products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: ASC}) &lbrace;
        total_count
        items &lbrace;
          name
          sku
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>
1. Überprüfen Sie die Antwort.
1. Ändern Sie in der GraphQL **Abfrage die Sortierreihenfolge von** ASC **in DESC**:
   <pre>
    <code class="language-graphql">
    &lbrace;
      products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: DESC}) &lbrace;
        total_count
        items &lbrace;
          name
          sku
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>
1. Überprüfen Sie die Antwort.

<u>Erwartete Ergebnisse</u>:

Die Produktliste in der GraphQL-Antwort sollte entsprechend der Sortierreihenfolge geändert werden.

<u>Tatsächliche Ergebnisse</u>:

Die Sortierreihenfolge bleibt unverändert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
