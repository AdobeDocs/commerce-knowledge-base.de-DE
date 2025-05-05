---
title: 'MDVA-40134: GraphQL gibt keine verwandten Produkte zurück, wenn der freigegebene Katalog aktiviert ist'
description: Der Patch MDVA-40134 behebt das Problem, dass GraphQL keine verwandten Produkte zurückgibt, wenn der freigegebene Katalog aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-40134. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: 7b14355a-1c14-4c80-9426-6c40505d638b
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-40134: GraphQL gibt keine verwandten Produkte zurück, wenn der freigegebene Katalog aktiviert ist

Der Patch MDVA-40134 behebt das Problem, dass GraphQL keine verwandten Produkte zurückgibt, wenn der freigegebene Katalog aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-40134. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

GraphQL gibt keine verwandten Produkte zurück, wenn der freigegebene Katalog aktiviert ist.

<u>Voraussetzungen</u>:

B2B-Module müssen installiert werden.
Die Instanz darf nur mit den Beispieldaten sauber sein.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **Stores** > **Konfiguration** > **Allgemein** > **B2B-Funktionen** und aktivieren Sie **Unternehmens- und freigegebenen Katalog**.
1. Navigieren Sie **Katalog** > **Freigegebener Katalog** und fügen Sie alle Produkte zum **Allgemeiner Katalog** hinzu.
1. Verwenden Sie die Beispieldaten und modifizieren Sie den Joust Duffle Bag (SKU 24-MB01).
1. Fügen **unter „Verwandte Produkte** die beiden Reisetaschen (ID 7 und 13) hinzu.
1. Senden einer **POST**-Anfrage:

<pre>&lbrace;
  products(filter: {sku: {eq: „24-MB01“}}, sort: {name: ASC}) &lbrace;
    items &lbrace;
      related_products &lbrace;
        UID
        -Name
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;</pre>

<u>Erwartete Ergebnisse</u>:

In der GraphQL-Antwort werden verwandte Produkte angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Benutzende erhalten die folgende Fehlermeldung:

<pre>Der Rückgabewert von Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor::getStoreId() muss vom Typ int sein, null zurückgegeben &lbrace;„Exception“:“[Objekt] (GraphQL\\Error\\Error(Code: 0): Der Rückgabewert von Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor::getStoreId() muss vom Typ int sein, null zurückgegeben </pre>

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in unserer Entwicklerdokumentation.
