---
title: 'MDVA-42768: GraphQL zeigt falschen Preis an, wenn untergeordnete Produkte nicht vorrätig sind'
description: Der Patch MDVA-42768 behebt das Problem, dass GraphQL den falschen Preis anzeigt, wenn die untergeordneten Produkte eines konfigurierbaren Produkts nicht vorrätig sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-42768. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: 012e7e21-e508-4449-98a6-4bdb41284c3a
feature: GraphQL, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# MDVA-42768: GraphQL zeigt falschen Preis an, wenn untergeordnete Produkte nicht vorrätig sind

Der Patch MDVA-42768 behebt das Problem, dass GraphQL den falschen Preis anzeigt, wenn die untergeordneten Produkte eines konfigurierbaren Produkts nicht vorrätig sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-42768. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn die untergeordneten Produkte eines konfigurierbaren Produkts nicht vorrätig sind und die Einstellung Nicht vorrätige Produkte anzeigen aktiviert ist, zeigt die GraphQL-Abfrage den regulären Preis des Produkts als **0** an.

<u>Voraussetzungen</u>:

Beispieldaten werden installiert.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie die Einstellung Nicht vorrätiges Produkt anzeigen in der Commerce-Admin, indem Sie zu **Stores** > **Configuration** > **Catalog** > **Inventory** gehen.
1. Erstellen Sie ein konfigurierbares Produkt und weisen Sie ihm ein einfaches untergeordnetes Produkt zu.
1. Legen Sie den Bestand des Varianten-(einfachen) Produkts auf „Nicht **&quot;**.
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

1. Überprüfen Sie den Abschnitt Antwort `minimum_price` > `regular price`.

<u>Erwartete Ergebnisse</u>:

Der reguläre Mindestpreis wird nicht als 0 angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Der reguläre Mindestpreis = 0 als Antwort.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
