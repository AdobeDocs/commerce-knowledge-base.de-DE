---
title: 'ACSD-47937: Preisabfallbenachrichtigungen werden aufgrund von Caching auf Anwendungsebene nicht gesendet'
description: Wenden Sie den Patch ACSD-47937 an, um das Adobe Commerce-Problem zu beheben, bei dem aufgrund des Caching auf Anwendungsebene nicht immer Preisabfallbenachrichtigungen gesendet werden.
exl-id: f39c9ef6-4689-427f-bd61-3a52dec88be2
feature: Admin Workspace, Cache, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-47937: Preisabfallbenachrichtigungen werden aufgrund von Caching auf Anwendungsebene nicht gesendet

Mit dem Patch ACSD-47937 wird das Problem behoben, dass aufgrund der Zwischenspeicherung auf Anwendungsebene nicht immer Preisabfallbenachrichtigungen gesendet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 installiert ist. Die Patch-ID ist ACSD-47937. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 und 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4, 2.4.5 und 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Kunden erhalten keine E-Mail zu Produktpreisrückgängen für nachfolgende Produktpreisänderungen.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie **[!UICONTROL Product Alert]** für *[!UICONTROL Price Changes]* und *[!UICONTROL Back in Stock]* in **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]**.
1. **[!UICONTROL Display Out of Stock Products]** aktivieren.
1. Einfaches Produkt (ABC) mit Menge = 0 erstellen.
1. Erstellen Sie eine Kundin oder einen Kunden aus der Storefront und abonnieren Sie das obige Produkt, um Produktbenachrichtigungen für Preisrückgänge zu erhalten.
1. Starten Sie den Warnhinweis für Kunden.

   ```PHP
   bin/magento queue:consumers:start product_alert
   ```

1. Senken Sie den Preis für das ABC-Produkt.
1. Trigger des Warnhinweiscron des Produkts.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Senken Sie den Preis für das ABC-Produkt erneut.
1. Trigger des Warnhinweiscron des Produkts.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

>[!NOTE]
>
>Wenn Sie mit [!DNL n98] Tool nicht vertraut sind, können Sie `bin/magento cron:run command` wie gewohnt ausführen und `cron_schedule` Tabelle überwachen, um sicherzustellen, dass `catalog_product_alert` Auftrag den Status „Erfolg“ erhält.

<u>Erwartete Ergebnisse</u>:

Die zweite Preis-Dropdown-E-Mail wird gesendet.

<u>Tatsächliche Ergebnisse</u>:

Die zweite Preis-Dropdown-E-Mail wird nicht gesendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
