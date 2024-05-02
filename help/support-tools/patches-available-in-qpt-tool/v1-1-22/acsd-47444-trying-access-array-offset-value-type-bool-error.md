---
title: '"ACSD-47444: _[!UICONTROL Trying to access array offset on value of type bool]_ Fehler beim Zugriff auf bestimmte nicht vorhandene Kategoriepfade für bekannte Produkte auf PHP 7.4'''
description: Wenden Sie den Patch ACSD-47444 an, um das Adobe Commerce-Problem zu beheben, bei dem ein _ vorhanden ist.[!UICONTROL Trying to access array offset on value of type bool]_ Fehler beim Zugriff auf bestimmte nicht vorhandene Kategoriepfade für bekannte Produkte, auf PHP 7.4.
exl-id: dfe803d0-bcff-40e6-a759-8c2243235ea8
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-47444: _[!UICONTROL Trying to access array offset on value of type bool]_Fehler beim Zugriff auf bestimmte nicht vorhandene Kategoriepfade für bekannte Produkte auf PHP 7.4

Der Patch ACSD-47444 löst das Problem, in dem Sie _[!UICONTROL Trying to access array offset on value of type bool]_Fehler beim Zugriff auf bestimmte nicht vorhandene Kategoriepfade für bekannte Produkte auf PHP 7.4. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22 installiert ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der folgende Fehler tritt auf: _[!UICONTROL Trying to access array offset on value of type bool]_beim Zugriff auf bestimmte nicht vorhandene Kategoriepfade für bekannte Produkte auf PHP 7.4.

<u>Voraussetzungen</u>:

PHP 7.4.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein neues Produkt mit dem Namen &quot;test&quot;.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** > set **[!UICONTROL Generate "category/product" URL Rewrites]** = _Nein_.
1. Gehen Sie zur Storefront und besuchen Sie die URL wie ../abc/test.html (&quot;abc&quot; - sollte nicht vorhanden sein).

<u>Erwartete Ergebnisse</u>:

404 Seite.

<u>Tatsächliche Ergebnisse</u>:

500-Fehler:

_[!UICONTROL Notice: Trying to access array offset on value of type bool in /app/code/Magento/CatalogUrlRewrite/Model/Storage/DynamicStorage.php on line 182]_

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
