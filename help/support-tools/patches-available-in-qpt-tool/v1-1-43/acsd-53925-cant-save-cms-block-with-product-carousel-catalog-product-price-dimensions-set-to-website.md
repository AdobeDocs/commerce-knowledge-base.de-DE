---
title: '"ACSD-53925: CMS-Block kann nicht gespeichert werden mit [!UICONTROL Product Carousel]'''
description: Wenden Sie den Patch ACSD-53925 an, um das Adobe Commerce-Problem zu beheben, bei dem der Administrator keinen CMS-Block mit dem Produktkarussell speichern kann, wenn der Dimensionsmodus für "catalog_product_price"auf "website"festgelegt ist.
feature: CMS, Page Builder, Price Indexer, Products
role: Admin, Developer
exl-id: 6ef6d8ff-4ebb-4adb-9fb7-0d4a81a25f50
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-53925: CMS-Block kann nicht gespeichert werden mit *[!UICONTROL Product Carousel]*

Der Patch ACSD-53925 behebt das Problem, dass der Administrator keinen CMS-Block mit *[!UICONTROL Product Carousel]* wann der Dimensionsmodus für `catalog_product_price` auf website festgelegt ist. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.43 ist installiert. Die Patch-ID ist ACSD-53925. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Admin kann einen CMS-Block nicht speichern mit *[!UICONTROL Product Carousel]* wann der Dimensionsmodus für `catalog_product_price` auf website festgelegt ist.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie zwei einfache Produkte:
   * simple1 - 10$
   * simple2 - 20$
1. Erstellen eines Bundle-Produkts *bundle1-dyn*&#39; mit zwei Optionen, die auf einfachen Produkt-SKUs basieren.
1. Legen Sie den Dimensionsmodus für den Produktpreisindex fest:

   `bin/magento indexer:set-dimensions-mode catalog_product_price website`

1. Navigieren Sie zu **[!UICONTROL Content]** > **[!UICONTROL Blocks]** und erstellen Sie einen neuen CMS-Block.
1. Bearbeiten Sie den Inhalt mit [!DNL Page Builder]:
   * Hinzufügen einer *[!UICONTROL Row]* element
   * Hinzufügen einer *[!UICONTROL Products]* element
   * Auswählen *[!UICONTROL Product Carousel]*
   * Produkt-SKU eingeben - *bundle1-dyn*
1. Speichern Sie den CMS-Block.

<u>Erwartete Ergebnisse</u>:

Benutzer können problemlos ein Produktkarussell hinzufügen.

<u>Tatsächliche Ergebnisse</u>:

* In der Benutzeroberfläche wird eine Meldung ausgegeben: *Es tut uns leid, beim Generieren dieses Inhalts ist ein Fehler aufgetreten.*
* `var/log/exception.log` enthält den folgenden Fehler:

  ```
  [2023-08-18T20:58:14.533374+00:00] report.CRITICAL: PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'username_dev.catalog_product_index_price_ws0' doesn't exist in /test/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
  ```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
