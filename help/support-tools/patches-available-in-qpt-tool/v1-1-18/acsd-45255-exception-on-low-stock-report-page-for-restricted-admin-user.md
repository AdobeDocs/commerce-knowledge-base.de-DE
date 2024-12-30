---
title: 'ACSD-45255: Ausnahme auf der Berichtsseite für niedrige Lagerbestände für eingeschränkte Admin-Benutzende'
description: Der Patch ACSD-45255 löst das Problem, dass auf der Seite „Low Stock Report“ eine Ausnahme für einen Benutzer mit eingeschränktem Administratorzugriff ausgelöst wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 installiert ist. Die Patch-ID ist ACSD-45255. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.
exl-id: 4b08500a-384e-4d5b-9563-3f9d1b984349
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-45255: Ausnahme auf der Berichtsseite für niedrige Lagerbestände für eingeschränkte Admin-Benutzende

Der Patch ACSD-45255 löst das Problem, dass auf der Seite „Low Stock Report“ eine Ausnahme für einen Benutzer mit eingeschränktem Administratorzugriff ausgelöst wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 installiert ist. Die Patch-ID ist ACSD-45255. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.5

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Auf der Seite „Low Stock-Bericht“ wird für einen eingeschränkten Admin-Benutzer eine Ausnahme ausgelöst.

<u>Voraussetzungen</u>:

* Die Inventarmodule sind aktiviert.
* Es gibt eine zusätzliche Website-, Store- und Store-Ansicht.
* Es gibt einen Admin-Benutzer, der nur über Zugriff auf die zusätzliche Website verfügt.

<u>Schritte zur Reproduktion</u>:

1. Öffnen Sie Commerce Admin als Benutzer mit eingeschränktem Administratorzugriff.
1. Navigieren Sie **Berichte** > **Produkte** > **Geringer Bestand**.

<u>Erwartete Ergebnisse</u>:

Der Bericht „Geringe Lagerbestände“ wird nur für Administratoren mit eingeschränkter Zugriffsberechtigung angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Es wird eine Ausnahme ausgelöst:

```bash
TypeError: Argument 1 passed to Magento\InventoryLowQuantityNotification\Model\ResourceModel\LowQuantityCollection\Interceptor::addStoreFilter() must be of the type int, array given, called in ../app/code/Magento/AdminGws/Plugin/CollectionFilter.php on line 101 and defined in ../generated/code/Magento/InventoryLowQuantityNotification/Model/ResourceModel/LowQuantityCollection/Interceptor.php:20
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in unserer Entwicklerdokumentation.
