---
title: 'ACSD-57846: GraphQL-Produkte suchen mit Filtern nach Nullpreisen, ohne Ergebnisse zurückzugeben'
description: Wenden Sie den Patch ACSD-57846 an, um das Adobe Commerce-Problem zu beheben, bei dem das Filtern von Produkten zum Preis von null zu einer fehlerhaften Anforderung zu [!DNL OpenSearch] führt und keine Ergebnisse zurückgibt.
feature: GraphQL, Products
role: Admin, Developer
exl-id: 6676cfec-b833-4895-a7c4-c81fcd042e54
source-git-commit: 06f751e43ef825c0eb29cb9b42eb41f07c308625
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-57846: GraphQL-Produkte suchen mit Filtern nach Nullpreisen, ohne Ergebnisse zurückzugeben

Der Patch ACSD-57846 behebt das Problem, dass das Filtern von Produkten zum Preis von null zu einer fehlerhaften Anforderung zu [!DNL OpenSearch] führt und keine Ergebnisse zurückgibt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 installiert ist. Die Patch-ID ist ACSD-57846. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Filtern von Produkten für den Preis von null in einer GraphQL-Produktsuche führt zu einer fehlerhaften Anfrage an [!DNL OpenSearch] und gibt keine Ergebnisse zurück.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Kategorie mit zwei einfachen Produkten:
   * simple1 - price $0
   * simple2 - Preis: 10 USD
1. Stellen Sie sicher, dass beide Produkte auf der Vorderseite sichtbar sind.
1. Senden Sie eine Anfrage mit `price:{from:"1"}`.

   ```graphql
   query {
     products(
       pageSize: 50
       currentPage: 1,
       filter: {price:{from:"1"}}
     ) {
       totalResult: total_count
       productItems: items {
         sku
         urlKey: url_key
         price: price_range {
           fullPrice: minimum_price {
             finalPrice: final_price {
               currency
               value
             }
           }
         }
       }
     }
   }
   ```

1. Dadurch wird das Produkt *simple2* zurückgegeben.
1. Senden Sie jetzt eine Anfrage mit `price:{from:"0"}`.

   ```graphql
   query {
     products(
       pageSize: 50
       currentPage: 1,
       filter: {price:{from:"0"}}
     ) {
       totalResult: total_count
       productItems: items {
         sku
         urlKey: url_key
         price: price_range {
           fullPrice: minimum_price {
             finalPrice: final_price {
               currency
               value
             }
           }
         }
       }
     }
   }
   ```

<u>Erwartete Ergebnisse</u>:

Beide Produkte, *simple1* und *simple2*, werden zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

Es werden keine Produkte zurückgegeben.

```json
{
    "data": {
        "products": {
            "totalResult": 0,
            "productItems": []
        }
    }
}
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
