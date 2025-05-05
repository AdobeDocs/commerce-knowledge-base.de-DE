---
title: 'ACSD-46856: Verbessert die Leistung bei der Aktualisierung der Stufenpreise'
description: Wenden Sie den ACSD-46856 Patch an, um die Leistung bei der Aktualisierung der Stufenpreise über System &gt; Konfiguration &gt; Import &gt; Advanced Pricing zu verbessern.
exl-id: c08560ef-94fa-4be4-9c59-d4b1b5e4186f
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-46856: Die Aktualisierung der Stufenpreise über „System“ > „Konfiguration“ > „Import“ > „Erweiterte Preise“ ist langsam

Der ACSD-46856 Patch verbessert die Leistung bei der Aktualisierung der Stufenpreise über **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Import]** > **[!UICONTROL Advanced Pricing]**. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 installiert ist. Die Patch-ID ist ACSD-46856. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Aktualisierung der Stufenpreise über **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Import]** > **[!UICONTROL Advanced Pricing]** verläuft langsam.

<u>Schritte zur Reproduktion</u>:

* Importieren Sie eine große Anzahl von Produkten (Beispiel: 10k+ oder 200k+) über **System** > **Konfiguration** > **Importieren** > **Erweiterte Preise**.

<u>Erwartete Ergebnisse</u>:

Mit dem Patch beträgt die Verarbeitungszeit für mehr als 200.000 Produkte etwa 1:00 Minuten.

<u>Tatsächliche Ergebnisse</u>:

Ohne Patch beträgt die Verarbeitungszeit für 10k+-Produkte etwa 10:00 Minuten.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
