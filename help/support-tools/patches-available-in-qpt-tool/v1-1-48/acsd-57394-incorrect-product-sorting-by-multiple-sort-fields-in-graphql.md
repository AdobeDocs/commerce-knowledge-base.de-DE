---
title: '"ACSD-57394: Falsche Produktsortierung nach mehreren Sortierungsattributen in [!DNL GraphQL]'''
description: Wenden Sie den Patch ACSD-57394 an, um das Adobe Commerce-Problem zu beheben, bei dem Produkte bei Verwendung mehrerer Sortierattribute in falsch sortiert werden. [!DNL GraphQL].
feature: GraphQL, Products
role: Admin, Developer
exl-id: f2e24daa-43a0-46b2-80b2-4e0ee116b776
source-git-commit: 42712af2ce4337cd64b8dea555139e4252fb91cf
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-57394: Falsche Produktsortierung nach mehreren Sortierungsattributen in [!DNL GraphQL]

Der Patch ACSD-57394 behebt das Problem, dass Produkte bei der Verwendung mehrerer Sortierattribute in falsch sortiert werden [!DNL GraphQL]. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 ist installiert. Die Patch-ID ist ACSD-57394. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.5.0 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Produkte werden bei Verwendung mehrerer Sortierattribute in falsch sortiert [!DNL GraphQL].

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einige Produkte mit unterschiedlichen Preisen und Namen.
1. Erstellen Sie eine Kategorie und weisen Sie ihr die erstellten Produkte zu.
1. Senden Sie eine [!DNL GraphQL] Produktabfrage für die erstellte Kategorie mit einigen *sort* -Attribute. Beispiel:

   ```
   {
   products(
     currentPage: 1
     pageSize: 10
     filter: {
       category_id: {
         eq :"3"
       }
     }
     sort: {  price: DESC, name: ASC, position: ASC
     }
   ){
   items{
     name
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
           }
      }
     }
    }
   ```

1. Überprüfen Sie die Antwort nach der Erstellung *sort* -Attribute.

<u>Erwartete Ergebnisse</u>:

Die Produkte sollten in der richtigen Reihenfolge zurückgegeben werden. Die Sortierung der Produkte nach mehreren Attributen sollte funktionieren.

<u>Tatsächliche Ergebnisse</u>:

Die Produkte werden nicht in der richtigen Reihenfolge zurückgegeben. Die Sortierung der Produkte nach mehreren Attributen funktioniert nicht.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.

