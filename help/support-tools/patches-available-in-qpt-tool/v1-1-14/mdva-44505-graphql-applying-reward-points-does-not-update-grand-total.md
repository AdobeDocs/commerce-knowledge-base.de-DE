---
title: 'MDVA-44505: GraphQL-Abfrage zur Anwendung von Belohnungspunkten im Warenkorb aktualisiert Gesamtsumme nicht'
description: Der Patch MDVA-44505 behebt das Problem, dass die GraphQL-Abfrage für einen Warenkorb, der belohnte Punkte anwendet, die Belohnungspunkte nicht berücksichtigt und einen falschen Gesamtwert zurückgibt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-44505. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: 724273ba-b020-4dba-88ae-94968bbd83de
feature: GraphQL, Orders, Rewards, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-44505: GraphQL-Abfrage zur Anwendung von Belohnungspunkten im Warenkorb aktualisiert Gesamtsumme nicht

Der Patch MDVA-44505 behebt das Problem, dass die GraphQL-Abfrage für einen Warenkorb, der belohnte Punkte anwendet, die Belohnungspunkte nicht berücksichtigt und einen falschen Gesamtwert zurückgibt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-44505. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die GraphQL-Abfrage für einen Warenkorb, der belohnte Punkte anwendet, berücksichtigt die Belohnungspunkte nicht und gibt einen falschen Gesamtwert zurück.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren von Belohnungspunkten.
1. Erstellen Sie einen Warenkorb und wenden Sie einige Belohnungspunkte an.
1. Rufen Sie die `GetCart` -Abfrage vom `GraphQL` -Endpunkt auf und rufen Sie Ihren Warenkorb ab:

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
1. Überprüfen Sie nun die Gesamtsumme des Warenkorbs des Kunden mithilfe der Rest-API (`/rest/V1/carts/mine/totals`).

<u>Erwartete Ergebnisse</u>:

Die GraphQL-Abfrage für den Warenkorb gibt die korrekte Gesamtsumme zurück, die die Belohnungspunkte berücksichtigt.

<u>Tatsächliche Ergebnisse</u>:

Die GraphQL-Abfrage berücksichtigt die Belohnungspunkte nicht und gibt einen falschen Gesamtwert zurück.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbar sind, in unserer Entwicklerdokumentation.
