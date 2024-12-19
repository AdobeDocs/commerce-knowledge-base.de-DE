---
title: 'MDVA-44505: Die GraphQL-Abfrage für die Anwendung von Prämienpunkten beim Warenkorb aktualisiert nicht die Gesamtsumme'
description: Der MDVA-44505 Patch löst das Problem, dass die GraphQL-Abfrage für einen Warenkorb, der Belohnungspunkte anwendet, die Belohnungspunkte nicht berücksichtigt und einen falschen Gesamtwert zurückgibt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-44505. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: 724273ba-b020-4dba-88ae-94968bbd83de
feature: GraphQL, Orders, Rewards, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-44505: Die GraphQL-Abfrage für die Anwendung von Prämienpunkten beim Warenkorb aktualisiert nicht die Gesamtsumme

Der MDVA-44505 Patch löst das Problem, dass die GraphQL-Abfrage für einen Warenkorb, der Belohnungspunkte anwendet, die Belohnungspunkte nicht berücksichtigt und einen falschen Gesamtwert zurückgibt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-44505. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die GraphQL-Abfrage für einen Warenkorb, in dem Belohnungspunkte angewendet werden, berücksichtigt die Belohnungspunkte nicht und gibt einen falschen Gesamtwert zurück.

<u>Schritte zur Reproduktion</u>:

1. Prämienpunkte konfigurieren.
1. Erstellen Sie einen Warenkorb und wenden Sie einige Prämienpunkte an.
1. Rufen Sie die `GetCart` Abfrage vom `GraphQL`-Endpunkt auf und rufen Sie Ihren Warenkorb ab:

   ```GraphQL
   query {
     cart(cart_id: "{CART_ID}") {
       prices {
         discounts {
           amount {
             value
           }
         }
         grand_total {
           value
         }
       }
     }
   }
   ```

1. Überprüfen Sie den Gesamteintrag.
1. Überprüfen Sie nun mit der REST-API (`/rest/V1/carts/mine/totals`) die Gesamtsumme des Warenkorbs des Kunden.

<u>Erwartete Ergebnisse</u>:

Die GraphQL-Abfrage für den Warenkorb gibt die richtige Gesamtsumme zurück, die die Belohnungspunkte berücksichtigt.

<u>Tatsächliche Ergebnisse</u>:

Die GraphQL-Abfrage berücksichtigt die Belohnungspunkte nicht und gibt einen falschen Gesamtwert zurück.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in unserer Entwicklerdokumentation.
