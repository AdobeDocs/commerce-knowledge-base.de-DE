---
title: 'ACSD-51305: Nicht vorrätige zusammengesetzte Kinderprodukte, die in der GraphQL-Antwort nicht verfügbar sind'
description: Wenden Sie den Patch ACSD-51305 an, um das Adobe Commerce-Problem zu beheben, bei dem nicht vorrätige zusammengesetzte untergeordnete Produkte in der GraphQL-Antwort nicht verfügbar sind.
exl-id: 0f33eb62-dfd3-4d07-b095-9ee6e9983c4d
feature: Categories, GraphQL, Orders, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-51305: Nicht vorrätige zusammengesetzte Kinderprodukte, die in der GraphQL-Antwort nicht verfügbar sind

Der Patch ACSD-51305 behebt das Problem, dass nicht vorrätige zusammengesetzte Kinderprodukte in der GraphQL-Antwort nicht verfügbar sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 installiert ist. Die Patch-ID ist ACSD-51305. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nicht vorrätige zusammengesetzte untergeordnete Produkte sind in der GraphQL-Antwort nicht verfügbar.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei der Admin-Website an.
1. Erstellen Sie eine Kategorie (cat1, id=3).
1. Erstellen Sie ein Produkt *simple1* (nicht vorrätig, nicht einzeln sichtbar, zugewiesen für *cat1*).
1. Erstellen Sie ein Produkt *simple2* (auf Lager, nicht einzeln sichtbar, zugewiesen für *cat1*).
1. Erstellen Sie ein Produkt *bundle1* mit den untergeordneten Produkten *simple1* und *simple2* als Optionsfeld *option1* und weisen Sie es der Kategorie *cat1* zu.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]**.

   * Setzen Sie **[!UICONTROL Display Out of Stock Products]** auf *Ja*.

1. Öffnen Sie das Produkt *bundle1* auf der Storefront und stellen Sie sicher, dass darin sowohl untergeordnete *simple1*- als auch untergeordnete *simple2*-Produkte angezeigt werden.
1. Führen Sie die folgende GraphQL-Abfrage aus:

   ```GraphQL
   {
       categoryList(filters: { ids: { in: ["3"] } }) {
           id
           name
           products(pageSize: 8, sort: { position: ASC }) {
               total_count
               items {
                   id
                   sku
                   name
                   ... on BundleProduct {
                       url_key
                       items {
                           title
                           sku
                           options {
                               quantity
                               position
                               is_default
                               product {
                                   id
                                   name
                                   sku
                               }
                           }
                       }
                   }
               }
           }
       }
   }
   ```

<u>Erwartete Ergebnisse</u>:

Der Abschnitt **[!UICONTROL Product]** innerhalb des Blocks **[!UICONTROL Options]** ist nicht leer.

<u>Tatsächliche Ergebnisse</u>:

Der Abschnitt **[!UICONTROL Product]** innerhalb des Blocks **[!UICONTROL Options]** ist leer.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
