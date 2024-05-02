---
title: Unsichtbar [!DNL reCAPTCHA] schlägt beim Auschecken fehl und verhindert die Platzierung der Bestellung
description: Wenden Sie den Patch ACSD-54656 an, um das Adobe Commerce-Problem zu beheben, bei dem das unsichtbare [!DNL reCAPTCHA] funktioniert beim Checkout nicht ordnungsgemäß, was die Platzierung einer Bestellung verhindert.
feature: Checkout, Gift
role: Admin, Developer
exl-id: dc26659e-ca34-461e-af91-b230c5afa919
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-54656: Unsichtbar [!DNL reCAPTCHA] funktioniert beim Checkout nicht ordnungsgemäß, was die Platzierung einer Bestellung verhindert.

Der Patch ACSD-54656 behebt das Problem, bei dem der unsichtbare [!DNL reCAPTCHA] funktioniert beim Checkout nicht ordnungsgemäß, was die Platzierung einer Bestellung verhindert. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 installiert ist. Die Patch-ID ist ACSD-54656. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Unsichtbar [!DNL reCAPTCHA] funktioniert beim Checkout nicht ordnungsgemäß, was die Platzierung einer Bestellung verhindert.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren beliebiger Typen von [!DNL reCAPTCHA] für die Geschenkkarte auf [!UICONTROL Checkout] Seite.
1. Produkt zum Warenkorb hinzufügen und zum **[!UICONTROL Checkout]** Seite.
1. Erweitern Sie das Formular für die Geschenkkarte und füllen Sie einen gültigen Gutschein für die Geschenkkarte aus.
1. Klicken Sie auf **[!UICONTROL See balance and apply]** Schaltfläche.

<u>Erwartete Ergebnisse</u>:

Die Geschenkkarte wurde erfolgreich angewendet.

<u>Tatsächliche Ergebnisse</u>:

Die Fehlermeldung wird angezeigt: *[!DNL reCAPTCHA]Validierung fehlgeschlagen, versuchen Sie es erneut.*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
