---
title: 'ACSD-51890: [!UICONTROL Submit review] Schaltfläche kann mehrmals angeklickt werden'
description: Wenden Sie den Patch ACSD-51890 an, um das Adobe Commerce-Problem zu beheben, bei dem die [!UICONTROL Submit Review]-Schaltfläche mehrmals ohne  [!DNL Google reCAPTCHA v3]  angeklickt werden kann.
feature: Products
role: Admin
exl-id: f6369a24-24bd-4e5e-a870-a13f507ada94
source-git-commit: 7dbf9a796fe2026b0657b719d10e5bb21b964fb6
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51890: **[!UICONTROL Submit Review]** Schaltfläche kann mehrmals ohne **[!DNL Google reCAPTCHA v3]** angeklickt werden

>[!NOTE]
>
>Dieser Patch wurde durch [ACSD-55112](/help/support-tools/patches-available-in-qpt-tool/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md) ersetzt.

Mit dem Patch ACSD-51890 wird das Problem behoben, dass die Schaltfläche **[!UICONTROL Submit Review]** mehrmals ohne **[!DNL Google reCAPTCHA v3]** Validierung angeklickt werden kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 installiert ist. Die Patch-ID ist ACSD-51890. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die **[!UICONTROL Submit Review]**-Schaltfläche kann mehrmals ohne **[!DNL Google reCAPTCHA v3]** Validierung angeklickt werden.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie **[!DNL Google reCAPTCHA v3]** für die Produktüberprüfung.
1. Öffnen Sie die Produktseite, navigieren Sie zum Abschnitt **[!UICONTROL Review]** und stellen Sie sicher, dass der [!DNL reCAPTCHA] sichtbar ist.
1. Füllen Sie das Überprüfungsformular aus und klicken Sie so schnell wie möglich mehrmals auf die Schaltfläche **[!UICONTROL Submit Review]** .
1. Öffnen Sie den **[!UICONTROL Review]** von der Administratorseite aus.

<u>Erwartete Ergebnisse</u>

Doppelte Überprüfungen werden nicht erstellt.

<u>Tatsächliche Ergebnisse</u>

Es werden doppelte Überprüfungen erstellt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de>) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de>) im [!DNL Quality Patches Tool].
