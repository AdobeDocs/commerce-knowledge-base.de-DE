---
title: 'ACSD-48773: E-Mail-Vorlage für Punkte-Bonuspunkte, die aus dem falschen Speicher genommen wurde'
description: Wenden Sie den Patch ACSD-48773 an, um das Adobe Commerce-Problem zu beheben, bei dem die E-Mail-Vorlage für die Punkte, die belohnt werden, aus dem falschen Store stammt.
exl-id: 96dda97c-5177-4883-ad2b-709928cb5f4d
feature: Admin Workspace, Communications, Marketing Tools, Orders, Personalization, Rewards
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-48773: E-Mail-Vorlage für Rewards-Punkte, die aus einem falschen Speicher stammt

Der Patch ACSD-48773 behebt das Problem, dass die E-Mail-Vorlage für die Punkte, die belohnt werden, aus dem falschen Speicher stammt. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 installiert ist. Die Patch-ID ist ACSD-48773. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Neuindizierung des Produktpreises funktioniert nicht, wenn das Paket-Produkt keiner Website zugewiesen ist.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie 2 Websites, 2 Stores und 2 Store-Ansichten.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Reviews]** und aktivieren **[!UICONTROL Reviews]**.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Store Email Addresses]**.
Wechseln Sie zu **[!DNL default website scope]** und legen Sie die **[!UICONTROL Customer Support Sender Email]** -Adresse (z. B.: *support_base@example.com*).
Wechseln Sie zu **[!DNL second website scope]** und legen Sie die **[!UICONTROL Customer Support Sender Email]** Adresse zu einem anderen Wert (z. B.: *support_second@example.com*).
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** > **[!UICONTROL Share Customer Accounts]** und legen **[!UICONTROL Share Customer Accounts]** = *Pro Website*.
1. under **[!UICONTROL Reward Points]**, legen Sie Folgendes fest:
   **[!UICONTROL Enable Reward Points Functionality]** = *Ja*
   **[!UICONTROL Enable Reward Points Functionality on Storefront]** = *Ja*
   **[!UICONTROL Actions for Acquiring Reward Points by Customers]** > **[!UICONTROL Review Submission]** und **[!UICONTROL Review Submission]** = *150*
   **[!UICONTROL Email Notification Settings]** > **[!UICONTROL Email Sender]** und **[!UICONTROL Email Sender]** = *Kundensupport*
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** und die Wechselkurse für die zweite Website für **[!UICONTROL Points/Currency]** und **[!UICONTROL Currency/Points]**.
1. Erstellen Sie auf der zweiten Website ein Kundenkonto.
1. Melden Sie sich als Kunde auf der zweiten Website an.
1. Aktivieren Sie **[!UICONTROL Subscribe]** für **[!UICONTROL Balance Updates]**.
1. Senden Sie eine Produktüberprüfung.
1. Navigieren Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL User Content]** > **[!UICONTROL Pending Reviews]**.
1. Ändern Sie den Status der neuen Überprüfung in ***[!UICONTROL Approved]*** und **[!UICONTROL Save]**.
1. Warten Sie, bis die E-Mail ankommt.

<u>Erwartete Ergebnisse</u>:

Die Update-E-Mail für die Prämienpunkte sollte vom E-Mail-Absender gesendet worden sein, der im zweiten Website-Bereich konfiguriert wurde.

<u>Tatsächliche Ergebnisse</u>:

Die Update-E-Mail für die Prämienpunkte wurde vom E-Mail-Absender gesendet, der im standardmäßigen Website-Bereich konfiguriert wurde.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
