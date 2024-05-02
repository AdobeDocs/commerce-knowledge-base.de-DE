---
title: "ACSD-52824: Für Unternehmenskunden angezeigte Zahlungsmethoden deaktiviert"
description: Wenden Sie den Patch ACSD-52824 an, um das Adobe Commerce-Problem zu beheben, bei dem [!DNL PayPal Express], [!DNL Google Pay], and [!DNL Apple Pay] Zahlungsmethoden werden für Unternehmenskunden angezeigt, obwohl sie in den Unternehmenseinstellungen deaktiviert sind.
feature: Payments, B2B, Shopping Cart
role: Admin, Developer
exl-id: 03496fb1-d492-4f02-9cdc-466cb571a2eb
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-52824: Deaktivierte Zahlungsmethoden für Unternehmenskunden

Der Patch ACSD-52824 behebt das Problem, bei dem [!DNL PayPal Express], [!DNL Google Pay], und [!DNL Apple Pay] Zahlungsmethoden werden für Unternehmenskunden angezeigt, obwohl sie in den Unternehmenseinstellungen deaktiviert sind. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 ist installiert. Die Patch-ID ist ACSD-52824. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Für Unternehmenskunden werden deaktivierte Zahlungsmethoden angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren und Aktivieren [!DNL PayPal Express Checkout]. Navigieren Sie zu **[!UICONTROL Basic Settings]** > Auswählen **[!DNL PayPal Express Checkout]** und legen Sie die Option für **[!UICONTROL Display on Shopping Cart]** nach *Ja*.
1. Konfigurieren [!DNL Braintree] und aktivieren [!DNL Apple Pay] und [!DNL Google Pay] bis [!DNL Braintree].
1. Navigieren Sie zu **[!UICONTROL Customers]** > **[!UICONTROL Companies]** und erstellen Sie ein neues Unternehmen.
1. Klicken Sie auf **[!UICONTROL Advanced Settings]**, suchen Sie die **[!UICONTROL Applicable Payment Methods]** und wählen **[!UICONTROL Selected Payment Methods]**.
1. under **[!UICONTROL Selected Payment Methods]** auswählen, die Zahlungsmethoden auswählen, die aktiviert sind und nicht mit *[!DNL PayPal Express Checkout]*, *[!DNL Apple Pay]* oder *[!DNL Google Pay]*. Wählen Sie beispielsweise **[!UICONTROL Check/Money Order]**.
1. Erstellen Sie nach Auswahl der entsprechenden Zahlungsmethoden einen neuen Kunden und verbinden Sie ihn mit dem zuvor erstellten Unternehmen.
1. Melden Sie sich mit dem Kundenkonto an, das dem Unternehmen zugeordnet ist, und fahren Sie mit dem Hinzufügen von Artikeln zum Warenkorb fort.
1. Beachten Sie beim Checkout-Prozess den Mini-Warenkorb, den Warenkorb und den Zahlungsschritt.

<u>Erwartete Ergebnisse</u>:

Zahlungsoptionen aus [!DNL PayPal] und [!DNL Braintree] sind nicht im Mini-Warenkorb und im Warenkorb sichtbar.

<u>Tatsächliche Ergebnisse</u>:

Zahlungsoptionen aus [!DNL PayPal] und [!DNL Braintree] bleiben im Mini-Warenkorb und im Warenkorb sichtbar.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
