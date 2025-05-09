---
title: 'ACSD-54961: Benutzer mit eingeschränktem Administratorzugriff können keine [!UICONTROL Product Review status] aktualisieren'
description: Wenden Sie den Patch ACSD-54961 an, um das Adobe Commerce-Problem zu beheben, bei dem ein eingeschränkter Admin-Benutzer den Produktüberprüfungsstatus nicht massenweise aktualisieren kann.
feature: Products
role: Admin, Developer
exl-id: 26c5bacd-21de-4533-a7b6-4acbacd38fec
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-54961: Benutzer mit eingeschränktem Administratorzugriff können keine [!UICONTROL Product Review status] aktualisieren

Mit dem Patch ACSD-54961 wird das Problem behoben, dass ein Benutzer mit eingeschränktem Administratorzugriff keine Massenaktualisierungen durchführen [!UICONTROL Product Review status]. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 installiert ist. Die Patch-ID ist ACSD-54961. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein Benutzer mit eingeschränkter Administratorberechtigung kann keine [!UICONTROL Product Review status] aktualisieren.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine zusätzliche Website-, Store- und Store-Ansicht.
1. Fügen Sie ein Produkt zum 2. Store hinzu und fügen Sie dann eine Überprüfung hinzu.
1. Erstellen Sie einen eingeschränkten Admin-Benutzer mit Zugriff nur auf den zweiten Store.
1. Melden Sie sich als eingeschränkter Admin-Benutzer an, gehen Sie dann zu **[!UICONTROL &#x200B; Marketings]** > **[!UICONTROL Reviews]** > **[!UICONTROL Mass Update]** und setzen Sie den **Status** auf *Genehmigt* oder *Ausstehend*.

<u>Erwartete Ergebnisse</u>:

Der eingeschränkte Admin-Benutzer kann Überprüfungen mithilfe der **[!UICONTROL Mass Update]**-Aktion aktualisieren.

<u>Tatsächliche Ergebnisse</u>:

Fehler beim Aktualisieren von Überprüfungen mithilfe **[!UICONTROL Mass Update]** Aktion.<br>
Die `var/log/exception.log` enthält einen ähnlichen Fehler:

```
report.CRITICAL: TypeError: array_intersect(): Argument #1 ($array) must be of type array, null given in app/code/Magento/AdminGws/Model/Models.php:439
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
