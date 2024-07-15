---
title: "MDVA-35569: FPT wird nicht in GraphQL angezeigt"
description: Der Patch MDVA-35569 behebt das Problem, wenn FPT (feste Produktsteuer) nicht in GraphQL angezeigt wird, wenn der Status im Warenkorb angegeben ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 installiert ist. Die Patch-ID lautet MDVA-35569. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.
exl-id: 3c38f7f9-9372-4f22-819c-c53efb9b5f78
feature: GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# MDVA-35569: FPT wird nicht in GraphQL angezeigt

Der Patch MDVA-35569 behebt das Problem, wenn FPT (feste Produktsteuer) nicht in GraphQL angezeigt wird, wenn der Status im Warenkorb angegeben ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 installiert ist. Die Patch-ID lautet MDVA-35569. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4-2.4.1-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie FPT.
1. Erstellen Sie ein Attribut (Beispiel: *weee\_tax*).
1. Erstellen Sie ein Testprodukt (Beispiel: *weetax*) mit dem hinzugefügten Attribut *weee\_tax* .
1. Weisen Sie Kalifornien oder einem anderen Status im Attribut *weee\_tax* FPT zu.
1. Erstellen Sie einen Kunden in GraphQL.
1. Erstellen Sie einen Warenkorb in GraphQL.
1. Fügen Sie das Produkt *weetax* mit GraphQL in den Warenkorb.
1. Abfragen des Warenkorbs:

```php
{cart(cart_id: "xxx") {    items {    id    product {    name    sku    price_range {    minimum_price {    final_price {    value    }    fixed_product_taxes {    label    amount {    value    }    }    }    maximum_price {    final_price {    value    }    fixed_product_taxes {    label    amount {    value    }    }    }    }    }    prices {    price {    value    }    }    quantity    }    prices {    subtotal_excluding_tax {    value    }    applied_taxes {    amount {    value    }    }    grand_total {    value    currency    }    discounts {    amount {    value    }    label    }    }}}
```

<u>Erwartete Ergebnisse</u>:

Der FPT würde wie erwartet normal ausgefüllt.

<u>Tatsächliche Ergebnisse</u>:

* Die FPT füllt nicht mit Daten und ist leer.
* Die Warenkorbabfrage gibt diese Antwort zurück:

```php
{
 "data": {
 "cart": {
 "items": [
 {
 "id": "1",
 "product": {
 "name": "fpt",
 "sku": "fpt",
 "price_range": {
 "minimum_price": {
 "final_price": {
 "value": 10
 },
 "fixed_product_taxes": []
 },
 "maximum_price": {
 "final_price": {
 "value": 10
 },
 "fixed_product_taxes": []
 }
 }
 },
 "prices": {
 "price": {
 "value": 10
 }
 },
 "quantity": 1
 }
 ],
 "prices": {
 "subtotal_excluding_tax": {
 "value": 10
 },
 "applied_taxes": [],
 "grand_total": {
 "value": 21,
 "currency": "USD"
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
