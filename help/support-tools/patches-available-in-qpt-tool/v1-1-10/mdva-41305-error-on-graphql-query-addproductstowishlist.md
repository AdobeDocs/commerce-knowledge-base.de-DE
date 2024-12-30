---
title: 'MDVA-41305: Fehler bei GraphQL Query addProductsToWishlist für konfigurierbare Produkte'
description: Der Patch MDVA-41305 löst das Problem, dass Benutzende einen Fehler in der GraphQL-Abfrage „addProductsToWishlist“ für konfigurierbare Produkte erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-41305. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: 97d4ee1c-19af-46c0-96b2-c2765899ed83
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-41305: Fehler bei GraphQL Query addProductsToWishlist für konfigurierbare Produkte

Der Patch MDVA-41305 löst das Problem, dass Benutzende einen Fehler in GraphQL Query `addProductsToWishlist` für konfigurierbare Produkte erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-41305. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn Benutzende von GraphQL konfigurierbare Produkte (mit/ohne Konfiguration) zur Wunschliste hinzufügen, können sie als Antwort keine konfigurierbaren SKUs und konfigurierbaren Optionen abrufen.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein konfigurierbares Produkt (mit einer blauen, grauen und einer benutzerdefinierten Option).
1. Öffnen Sie das Frontend, melden Sie sich als Kunde an und erstellen Sie eine Wunschliste (check wishlist_id).
1. Öffnen Sie Postman und erstellen Sie ein Kunden-Token:

   <pre>
    <code class="language-graphql">
    mutation {
      generateCustomerToken(email: "", password: "") {
        token
      }
     }
     </code>
     </pre>

1. Legen Sie dieses Token für die Bearer-Autorisierung fest.
1. Versuchen Sie, ein konfigurierbares Produkt *Blau* zur Wunschliste hinzuzufügen, indem Sie folgende Anweisungen befolgen:

<pre>
<code class="language-graphql">
mutation {
 addProductsToWishlist(
   wishlistId: 1
   wishlistItems: [
     {
       sku: "conf2"
       selected_options: [
            "Y29uZmlndXJhYmxlLzkzLzUw"
       ]
       quantity: 1
       entered_options: [
         {
           uid: "Y3VzdG9tLW9wdGlvbi8x"
           value: "test"
         }
       ]
     }
    ]
  ) {
    wishlist {
      id
      items_count
      items_v2 (currentPage: 1, pageSize: 8 ) {
        items {
         id
         quantity
         ... on ConfigurableWishlistItem  {
           child_sku
           customizable_options {
             customizable_option_uid
           }
         }
         product {
           uid
           name
           sku
           options_container
           ... on CustomizableProductInterface {
             options {
              title
              required
              sort_order
              option_id
              ... on CustomizableFieldOption {
                value {
                  uid
                  sku
                  price
                  price_type
                  max_characters
                }
              }
            }
          }
          price_range {
            minimum_price {
              regular_price {
                currency
                value
              }
            }
            maximum_price {
               regular_price {
                 currency
                 value
               }
             }
           }
         }
       }
     }
   }
  user_errors {
    code
    message
   }
 }
}
</code>
</pre>

<u>Erwartete Ergebnisse</u>:

Benutzer können eine Reihe konfigurierter Produktoptionen in der Antwort sehen, die in der Payload angegeben und zur Wunschliste hinzugefügt wurde.

<u>Tatsächliche Ergebnisse</u>:

Benutzende erhalten als Antwort *Interner Server* Fehler.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in unserer Entwicklerdokumentation.
