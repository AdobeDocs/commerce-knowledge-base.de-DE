---
title: "ACSD-45817: GraphQL-Produktmutation gibt alle konfigurierbaren Varianten an"
description: Der Patch ACSD-45817 behebt das Problem, dass eine GraphQL-Mutation "products"für einen bestimmten Store alle konfigurierbaren Varianten zurückgibt, einschließlich der Varianten, die dem angeforderten Store nicht zugewiesen sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 installiert ist. Die Patch-ID lautet ACSD-45817. Beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.
exl-id: 3d61d1aa-36b5-471d-929b-7df8ce65c791
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-45817: Die GraphQL-Produktmutation liefert alle konfigurierbaren Varianten

Der Patch ACSD-45817 behebt das Problem, bei dem ein GraphQL `products` Die Mutation für einen bestimmten Store gibt alle konfigurierbaren Varianten zurück, einschließlich der Varianten, die dem angeforderten Store nicht zugewiesen sind. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 installiert ist. Die Patch-ID lautet ACSD-45817. Beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

A GRAPHQL `products` Die Mutation für einen bestimmten Store gibt alle konfigurierbaren Varianten zurück, einschließlich der Varianten, die dem angeforderten Store nicht zugewiesen sind.

<u>Voraussetzungen</u>:

Erstellen Sie eine zweite Website, einen zweiten Store und eine zweite Store-Ansicht.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit zwei Unterprodukten: &quot;konfigurable-a&quot;und &quot;configuring-b&quot;.
1. Weisen Sie das konfigurierbare Produkt beiden Websites zu.
1. Weisen Sie der zweiten Website nur eine &quot;konfigurierbare a&quot;-Variante zu.
1. Navigieren Sie zu **Storefront**, wechseln Sie zur zweiten Website und öffnen Sie das konfigurierbare Produkt.
1. Stellen Sie sicher, dass nur eine untergeordnete Option angezeigt wird: &quot;konfigurierbar-a&quot;.
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

Die &quot;konfigurierbare b&quot;-Variante wird der zweiten Website nicht zugewiesen und sollte nicht in der Antwort angezeigt werden.

<u>Tatsächliche Ergebnisse</u>:

Die Variante &quot;konfigurierbar-b&quot;wird in der Antwort angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
