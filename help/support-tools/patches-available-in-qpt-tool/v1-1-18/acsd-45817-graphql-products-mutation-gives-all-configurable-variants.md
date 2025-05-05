---
title: 'ACSD-45817: Die Mutation von GraphQL-Produkten bietet alle konfigurierbaren Varianten'
description: Der Patch ACSD-45817 behebt das Problem, dass eine GraphQL „products“-Mutation für einen bestimmten Store alle konfigurierbaren Varianten zurückgibt, einschließlich der Varianten, die dem angeforderten Store nicht zugewiesen sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 installiert ist. Die Patch-ID ist ACSD-45817. Beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.
exl-id: 3d61d1aa-36b5-471d-929b-7df8ce65c791
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-45817: Die Mutation von GraphQL-Produkten bietet alle konfigurierbaren Varianten

Mit dem Patch ACSD-45817 wird das Problem behoben, dass eine GraphQL-`products`-Mutation für einen bestimmten Store alle konfigurierbaren Varianten zurückgibt, einschließlich der Varianten, die dem angeforderten Store nicht zugewiesen sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 installiert ist. Die Patch-ID ist ACSD-45817. Beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p3

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Eine GraphQL `products`-Mutation für einen bestimmten Store gibt alle konfigurierbaren Varianten zurück, einschließlich der Varianten, die dem angeforderten Store nicht zugewiesen sind.

<u>Voraussetzungen</u>:

Erstellen Sie eine zweite Website, einen zweiten Store und eine zweite Store-Ansicht.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit zwei Unterprodukten: „configurable-a“ und „konfigurable-b“.
1. Weisen Sie beiden Websites das konfigurierbare Produkt zu.
1. Weisen Sie der zweiten Website nur eine Variante des Typs „konfigurierbar-a“ zu.
1. Wechseln Sie zur **Storefront**, zur zweiten Website und öffnen Sie das konfigurierbare Produkt.
1. Stellen Sie sicher, dass Sie nur eine untergeordnete Option sehen: „configurable-a“.
1. Ausführen einer GraphQL-Abfrage mit `POST: /graphql` Endpunkt und `Headers: "store" = "new"`

   ```GraphQL
   {
     products(filter: { sku: { eq: "configurable" } }) {
       items {
         id
         attribute_set_id
         name
         sku
         __typename
         price_range{
           minimum_price{
             regular_price{
               value
               currency
             }
           }
         }
         categories {
           id
         }
         ... on ConfigurableProduct {
           configurable_options {
             id
             attribute_id_v2
             label
             position
             use_default
             attribute_code
             values {
               value_index
               label
             }
             product_id
           }
           variants {
             product {
               id
               name
               sku
               attribute_set_id
               ... on PhysicalProductInterface {
                 weight
               }
               price_range{
                 minimum_price{
                   regular_price{
                     value
                     currency
                   }
                 }
               }
             }
             attributes {
               uid
               label
               code
               value_index
             }
           }
         }
       }
     }
   }
   ```

<u>Erwartete Ergebnisse</u>:

Die Variante „konfigurierbar-b“ ist der zweiten Website nicht zugewiesen und sollte in der Antwort nicht angezeigt werden.

<u>Tatsächliche Ergebnisse</u>:

Die Variante „konfigurierbar-b“ wird in der Antwort angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
