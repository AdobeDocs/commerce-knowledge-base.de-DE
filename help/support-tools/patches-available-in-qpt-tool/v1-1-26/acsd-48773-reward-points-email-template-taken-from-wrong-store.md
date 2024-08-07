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

Der Patch ACSD-48773 behebt das Problem, dass die E-Mail-Vorlage für die Punkte, die belohnt werden, aus dem falschen Speicher stammt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 installiert ist. Die Patch-ID ist ACSD-48773. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Neuindizierung des Produktpreises funktioniert nicht, wenn das Paket-Produkt keiner Website zugewiesen ist.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie 2 Websites, 2 Stores und 2 Store-Ansichten.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Reviews]** und aktivieren Sie **[!UICONTROL Reviews]**.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Store Email Addresses]**.
Wechseln Sie zu &quot;**[!DNL default website scope]**&quot;und legen Sie die Adresse &quot;**[!UICONTROL Customer Support Sender Email]**&quot;fest (z. B. *support_base@example.com*).
Wechseln Sie zu &quot;**[!DNL second website scope]**&quot;und legen Sie die Adresse &quot;**[!UICONTROL Customer Support Sender Email]**&quot;auf einen anderen Wert fest (z. B. *support_second@example.com*).
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** > **[!UICONTROL Share Customer Accounts]** und legen Sie **[!UICONTROL Share Customer Accounts]** = *pro Website* fest.
1. Legen Sie unter **[!UICONTROL Reward Points]** Folgendes fest:
   **[!UICONTROL Enable Reward Points Functionality]** = *Ja*
   **[!UICONTROL Enable Reward Points Functionality on Storefront]** = *Ja*
   **[!UICONTROL Actions for Acquiring Reward Points by Customers]** > **[!UICONTROL Review Submission]** und legen **[!UICONTROL Review Submission]** = *150* fest
   **[!UICONTROL Email Notification Settings]** > **[!UICONTROL Email Sender]** und legen **[!UICONTROL Email Sender]** = *Kundenunterstützung* fest.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** und richten Sie die Wechselkurse für die zweite Website sowohl für **[!UICONTROL Points/Currency]** als auch für **[!UICONTROL Currency/Points]** ein.
1. Erstellen Sie auf der zweiten Website ein Kundenkonto.
1. Melden Sie sich als Kunde auf der zweiten Website an.
1. Stellen Sie sicher, dass Sie **[!UICONTROL Subscribe]** für **[!UICONTROL Balance Updates]** aktivieren.
1. Senden Sie eine Produktüberprüfung.
1. Gehen Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL User Content]** > **[!UICONTROL Pending Reviews]**.
1. Ändern Sie den Status der neuen Überprüfung in ***[!UICONTROL Approved]*** und **[!UICONTROL Save]**.
1. Warten Sie, bis die E-Mail ankommt.

<u>Erwartete Ergebnisse</u>:

Die Update-E-Mail für die Prämienpunkte sollte vom E-Mail-Absender gesendet worden sein, der im zweiten Website-Bereich konfiguriert wurde.

<u>Tatsächliche Ergebnisse</u>:

Die Update-E-Mail für die Prämienpunkte wurde vom E-Mail-Absender gesendet, der im standardmäßigen Website-Bereich konfiguriert wurde.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
