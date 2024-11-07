---
title: "MDVA-42768: GraphQL zeigt falschen Preis an, wenn Kinderprodukte nicht vorrätig sind"
description: Der Patch MDVA-42768 behebt das Problem, dass GraphQL den falschen Preis anzeigt, wenn ein konfigurierbares Produkt nicht mehr vorrätig ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-42768. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: 012e7e21-e508-4449-98a6-4bdb41284c3a
feature: GraphQL, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# MDVA-42768: GraphQL zeigt falschen Preis an, wenn Kinderprodukte nicht vorrätig sind

Der Patch MDVA-42768 behebt das Problem, dass GraphQL den falschen Preis anzeigt, wenn ein konfigurierbares Produkt nicht mehr vorrätig ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-42768. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn die untergeordneten Produkte eines konfigurierbaren Produkts nicht vorrätig sind und die Einstellung &quot;Nicht vorrätige Produkte anzeigen&quot;aktiviert ist, zeigt die GraphQL-Abfrage den regulären Produktpreis als **0** an.

<u>Voraussetzungen</u>:

Beispieldaten sind installiert.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie die Produkteinstellung &quot;Nicht auf Lager anzeigen&quot;in Commerce Admin, indem Sie zu **Stores** > **Konfiguration** > **Katalog** > **Inventar** navigieren.
1. Erstellen Sie ein konfigurierbares Produkt und weisen Sie ihm ein einfaches untergeordnetes Produkt zu.
1. Setzen Sie das Inventar der Variante (einfaches) Produkt auf **Nicht auf Lager**.
1. Neuindizieren.
1. Führen Sie die folgende GraphQL-Abfrage aus:

   ```GraphQL
   query {
     products(filter: { sku: { eq: "MH01" } }) {
       items {
         sku
         price_range {
           minimum_price {
             regular_price {
               value
               currency
             }
             final_price {
               value
               currency
             }
             discount {
               amount_off
               percent_off
             }
           }
           maximum_price {
             regular_price {
               value
               currency
             }
             final_price {
               value
               currency
             }
             discount {
               amount_off
               percent_off
             }
           }
         }
       }
     }
   }
   ```

1. Überprüfen Sie den Antwortabschnitt `minimum_price` > `regular price`.

<u>Erwartete Ergebnisse</u>:

Der reguläre Mindestpreis wird als Antwort nicht als 0 angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Der reguläre Mindestpreis = 0 als Antwort.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbar sind, in unserer Entwicklerdokumentation.
