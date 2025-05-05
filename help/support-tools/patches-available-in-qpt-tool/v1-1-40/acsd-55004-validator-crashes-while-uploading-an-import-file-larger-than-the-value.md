---
title: 'ACSD-55004: Der Validator stürzt beim Hochladen einer Importdatei ab, die größer als der Wert ist'
description: Wenden Sie den Patch ACSD-55004 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Validator beim Hochladen einer Importdatei, die größer ist als der in „php.ini“ konfigurierte Wert, abstürzt.
feature: Data Import/Export
role: Admin, Developer
exl-id: 03b7667e-9b5b-4319-9135-dbc7fda7861d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-55004: Der Validator stürzt beim Hochladen einer Importdatei ab, die größer als der Wert ist

Mit dem Patch ACSD-55004 wird das Problem behoben, dass ein Validator beim Hochladen einer Importdatei, die größer ist als der in `php.ini` konfigurierte Wert, abstürzt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.40 installiert ist. Die Patch-ID ist ACSD-55004. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Validator stürzt beim Hochladen einer Importdatei ab, die größer ist als der in `php.ini` konfigurierte Wert.

<u>Schritte zur Reproduktion</u>:

Versuchen Sie, eine Importdatei hochzuladen, die größer ist als in `php.ini` konfiguriert.

<u>Erwartete Ergebnisse</u>:

Die Dateigröße wird fehlerfrei validiert.

<u>Tatsächliche Ergebnisse</u>:

Validator stürzt ab.

`var/log/exception.log` enthält:

```
[2023-10-06T21:36:30.470618+00:00] report.CRITICAL: Error: Class "Zend_Validate_File_Upload" not found in ../module-import-export/Model/Source/Upload.php:81
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
