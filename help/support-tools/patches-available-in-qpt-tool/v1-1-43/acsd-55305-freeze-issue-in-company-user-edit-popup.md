---
title: '''ACSD-55305: Popup-Einfrieren während der Bearbeitung durch Unternehmensbenutzer in [!UICONTROL My Account]'
description: Wenden Sie den Patch ACSD-55305 an, um das Adobe Commerce-Problem zu beheben, bei dem das Popup-Fenster [!UICONTROL Edit Company User] auf der Seite [!UICONTROL My Account] &gt; [!UICONTROL Company Structure] mit einem Lader auf dem Bildschirm friert.
feature: Companies, B2B
role: Admin, Developer
exl-id: be2bfe08-d05e-485d-84c3-2ff14e1a8654
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-55305: Popup beim Bearbeiten des Unternehmens-Benutzers in [!UICONTROL My Account] frieren

Der Patch ACSD-55305 behebt das Problem, dass das [!UICONTROL Edit Company User]-Popup auf der Seite [!UICONTROL My Account]> [!UICONTROL Company Structure] mit einem Lader auf dem Bildschirm friert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 installiert ist. Die Patch-ID ist ACSD-55305. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Versuch, das Popup *[!UICONTROL Edit Company User]* auf der Seite *[!UICONTROL My Account]* > *[!UICONTROL Company Structure]* zu verwenden, tritt ein Fehler auf, da es mit einem Lader auf dem Bildschirm friert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein B2B-Unternehmen.
1. Erstellen Sie ein Attribut mit Mehrfachauswahl für Kunden.
1. Weisen Sie dem neu erstellten Attribut für den Unternehmensadministrator einen Wert zu.
1. Melden Sie sich als Unternehmensadministrator an.
1. Navigieren Sie zum [!UICONTROL account dashboard] und navigieren Sie zum **[!UICONTROL Company Structure]**.
1. Wählen Sie den Benutzer aus.
1. Klicken Sie auf **[!UICONTROL Edit Selected]**.

<u>Erwartete Ergebnisse</u>:

Das Formular-Popup wird korrekt angezeigt und bietet die Möglichkeit, Unternehmensinformationen zu bearbeiten.

<u>Tatsächliche Ergebnisse</u>:

Das Formular-Popup wird ohne Bearbeitungsmöglichkeit angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
