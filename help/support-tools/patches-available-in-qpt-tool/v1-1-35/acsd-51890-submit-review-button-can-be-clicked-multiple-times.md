---
title: "ACSD-51890: [!UICONTROL Submit review] -Schaltfläche kann mehrmals angeklickt werden."
description: Wenden Sie den Patch ACSD-51890 an, um das Adobe Commerce-Problem zu beheben, bei dem das [!UICONTROL Submit Review] -Schaltfläche kann mehrmals ohne [!DNL Google reCAPTCHA v3] Validierung.
feature: Products
role: Admin
exl-id: f6369a24-24bd-4e5e-a870-a13f507ada94
source-git-commit: 7dbf9a796fe2026b0657b719d10e5bb21b964fb6
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51890: **[!UICONTROL Submit Review]** -Schaltfläche kann mehrmals ohne **[!DNL Google reCAPTCHA v3]** Validierung

>[!NOTE]
>
>Dieser Patch wird durch [ACSD-55112](/help/support-tools/patches-available-in-qpt-tool/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md).

Der Patch ACSD-51890 behebt das Problem, bei dem das **[!UICONTROL Submit Review]** -Schaltfläche kann mehrmals ohne **[!DNL Google reCAPTCHA v3]** Validierung. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 installiert ist. Die Patch-ID ist ACSD-51890. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die **[!UICONTROL Submit Review]** -Schaltfläche kann mehrmals ohne die **[!DNL Google reCAPTCHA v3]** Validierung.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren **[!DNL Google reCAPTCHA v3]** für die Produktüberprüfung.
1. Öffnen Sie die Produktseite und navigieren Sie zur **[!UICONTROL Review]** und stellen Sie sicher, dass [!DNL reCAPTCHA] sichtbar ist.
1. Füllen Sie das Überprüfungsformular aus und klicken Sie auf **[!UICONTROL Submit Review]** so schnell wie möglich mehrmals auf.
1. Öffnen Sie die **[!UICONTROL Review]** aus dem Admin.

<u>Erwartete Ergebnisse</u>

Doppelte Überprüfungen werden nicht erstellt.

<u>Tatsächliche Ergebnisse</u>

Es werden doppelte Überprüfungen erstellt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] Handbuch.
