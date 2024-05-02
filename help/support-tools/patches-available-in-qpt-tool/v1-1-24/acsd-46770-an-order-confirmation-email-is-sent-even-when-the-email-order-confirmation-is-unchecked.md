---
title: '"ACSD-46770: Bestellbestätigungs-E-Mail wird gesendet, auch wenn [!UICONTROL Email Order Confirmation] ist deaktiviert'''
description: Wenden Sie den Patch ACSD-46770 an, um das Adobe Commerce-Problem zu beheben, bei dem Bestellbestätigungs-E-Mails auch dann gesendet werden, wenn [!UICONTROL Email Order Confirmation] nicht ausgewählt ist.
exl-id: 9cbf3a57-1f59-4030-b432-0e6cad410a27
feature: Communications, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46770: Bestellbestätigungs-E-Mail wird gesendet, auch wenn **[!UICONTROL Email Order Confirmation]** deaktiviert ist

Der Patch ACSD-46770 behebt das Problem, dass Bestellungen auch dann über die REST-API als Gastbenutzer aufgegeben werden können, wenn **[!UICONTROL Email Order Confirmation]** deaktiviert ist. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 ist installiert. Die Patch-ID ist ACSD-46770. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eine Bestellbestätigungs-E-Mail wird auch dann gesendet, wenn **[!UICONTROL Email Order Confirmation]** nicht ausgewählt ist.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Kundenkonto.
1. Navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Order]** und auf  **[!UICONTROL Create New Order]**.
1. Wählen Sie den Kunden aus, fügen Sie die Produkte zur Bestellung hinzu, geben Sie die Adresse ein und wählen Sie die Versand- und Zahlungsmethoden aus.
1. Deaktivieren Sie vor dem Senden der Bestellung die **[!UICONTROL Email Order confirmation]** aktivieren.
1. Klicken Sie auf **[!UICONTROL Submit Order]** , um die Bestellung zu erstellen.

<u>Erwartete Ergebnisse</u>:

Eine Bestellbestätigungs-E-Mail sollte nicht gesendet werden, wenn die **[!UICONTROL Email Order Confirmation]** deaktiviert ist.

<u>Tatsächliche Ergebnisse</u>:

Eine Bestätigungs-E-Mail wird unabhängig von der nicht ausgewählten E-Mail gesendet **[!UICONTROL Email Order Confirmation]** aktivieren.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
