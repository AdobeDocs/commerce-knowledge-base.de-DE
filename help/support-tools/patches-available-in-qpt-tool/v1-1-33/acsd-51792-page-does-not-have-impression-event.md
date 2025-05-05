---
title: 'ACSD-51792: Seite hat kein Impression-Ereignis'
description: Wenden Sie den Patch „ACSD-51792“ an, um das Leistungsproblem von Adobe Commerce zu beheben, bei dem eine Seite nicht das Impression-Ereignis aufweist, wenn Google Tag Manager 4 aktiviert ist.
exl-id: 59194d4c-c387-4372-a0ff-1cdd74f8c6df
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-51792: Seite hat kein Impression-Ereignis

Mit dem Patch ACSD-51792 wird das Leistungsproblem behoben, bei dem eine Seite das Impression-Ereignis nicht aufweist, wenn [!DNL Google Tag Manager] 4 aktiviert ist. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.33 installiert ist. Die Patch-ID ist ACSD-51792. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Seite hat kein Impression-Ereignis, wenn [!DNL Google Tag Manager] 4 aktiviert ist.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**.
1. Konfigurieren Sie die **[!DNL GoogleTag Manager]**.
1. Wechseln Sie zu [Google Tag Assistant](https://tagassistant.google.com/) und führen Sie die Schritte aus, die zum Herstellen einer Verbindung mit Ihrer Website erforderlich sind.
1. Öffnen Sie eine Kategorieseite, die in der Storefront eine Produktliste enthält.
1. Prüfen Sie im Tag-Assistenten-Beobachter, ob das Ereignis „impressions“ auftritt.

<u>Erwartete Ergebnisse</u>:

Das Impression-Ereignis sollte mit allen Produkten auf der Seite beginnen.

<u>Tatsächliche Ergebnisse</u>:

Die Seite verfügt nicht über das Impression-Ereignis im Tag-Assistenten-Beobachter.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
