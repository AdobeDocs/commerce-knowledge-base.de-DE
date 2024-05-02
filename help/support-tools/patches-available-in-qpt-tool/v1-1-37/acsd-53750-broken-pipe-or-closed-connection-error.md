---
title: '"ACSD-53750: "Broken pipe or closed connection" error during multi-threaded catalog_product_price reindex"'
description: Wenden Sie den Patch ACSD-53750 an, um das Adobe Commerce-Problem zu beheben, bei dem während der Neuindizierung des Multi-Thread-Katalogprodukts_Preises ein Fehler wegen eines *defekten Pfads oder einer geschlossenen Verbindung* auftritt.
feature: Products
role: Admin, Developer
exl-id: afb30384-74e7-4857-9aff-8e99f5abc309
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-53750: *Beschädigte Leitung oder geschlossene Verbindung* Fehler bei mehrprozessgestützten `catalog_product_price` reindex

Der Patch ACSD-53750 behebt das Problem, bei dem ein *Beschädigte Leitung oder geschlossene Verbindung* Fehler tritt während mehrprozessgestützter `catalog_product_price` reindex. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.37 installiert ist. Die Patch-ID ist ACSD-53750. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

*Beschädigte Leitung oder geschlossene Verbindung* Fehler tritt während mehrprozessgestützter `catalog_product_price` reindex.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie RabbitMq.
1. Beispieldaten mithilfe des angehängten `small.xml` -Datei.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** und **[!UICONTROL Stock/Source reindex strategy]** = **[!UICONTROL Asynchronous]**.
1. Legen Sie den Dimensionsmodus für Indizes fest, die dies unterstützen. Beispiel: `catalog_product_price_website_and_customer_group` oder `customer_group`.

   ```
   bin/magento indexer:set-dimensions-mode catalog_product_price customer_group
   ```

1. Zurücksetzen von Indexern ausführen für `catalog_product_price`.

   ```
   bin/magento indexer:reset catalog_product_price
   ```

1. Führen Sie den Indexer für den Reset-Indexer mit mehreren Threads aus.

   ```
   MAGE_INDEXER_THREADS_COUNT=10 bin/magento indexer:reindex catalog_product_price
   ```

<u>Erwartete Ergebnisse</u>:

Es treten keine Fehler auf.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler wird durch eine AMQP-Verbindung verursacht: *Beschädigte Leitung oder geschlossene Verbindung*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
