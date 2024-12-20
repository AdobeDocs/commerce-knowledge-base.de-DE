---
title: 'ACSD-56621: Aktualisierte Namen werden in der Grußkopfzeile für Unternehmensadministratoren nicht angezeigt'
description: Wenden Sie den Patch ACSD-56621 an, um das Adobe Commerce-Problem zu beheben, bei dem der aktualisierte Vor- und Nachname des Unternehmensadministrators nicht im Grußkopfbereich angezeigt wird.
feature: Companies, B2B, User Account
role: Admin, Developer
exl-id: 4ad9c878-b617-4e6a-939c-be15faf7124b
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-56621: Aktualisierte Namen werden in der Grußkopfzeile für Unternehmensadministratoren nicht angezeigt

Der Patch ACSD-56621 behebt das Problem, dass der aktualisierte Vor- und Nachname des Unternehmensadministrators nicht im Grußkopfbereich angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 installiert ist. Die Patch-ID ist ACSD-56621. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die aktualisierten Namen werden nicht in der Grußkopfzeile für Unternehmensadministratoren angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zum Bedienfeld &quot;**[!UICONTROL Admin]**&quot;.
1. Gehen Sie zu **[!UICONTROL Stores]** und wählen Sie **[!UICONTROL Configuration]** aus.
1. Wählen Sie unter dem Abschnitt **[!UICONTROL General]** die Option **[!UICONTROL B2B]** aus, um die Funktionalität des B2B-Unternehmens zu aktivieren.
1. Gehen Sie zu &quot;**[!UICONTROL Storefront]**&quot;und registrieren Sie ein neues Unternehmen.
1. Melden Sie sich als Unternehmensadministrator an.
1. Wechseln Sie zu **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** und ändern Sie die Vor- und Nachname-Felder nach Bedarf.

<u>Erwartete Ergebnisse</u>:

Der Vor- und Nachname des Benutzers im Grußkopfbereich wird sofort geändert.

<u>Tatsächliche Ergebnisse</u>:

Der Vor- und Nachname des Benutzers wird nur geändert, wenn sich der Benutzer abmeldet und sich erneut anmeldet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
