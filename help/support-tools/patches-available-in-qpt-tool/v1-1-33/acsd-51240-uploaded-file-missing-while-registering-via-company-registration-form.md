---
title: 'ACSD-51240: Hochgeladene Datei fehlt bei der Registrierung über das Formular für die Unternehmensregistrierung'
description: Wenden Sie den Patch ACSD-51240 an, um das Adobe Commerce-Problem zu beheben, bei dem die hochgeladene Datei bei der Registrierung über das Registrierungsformular für das Unternehmen fehlt.
exl-id: e5822c54-4e77-46b0-84b6-5e25c3845974
source-git-commit: e1fe8936c56f422ae591c6424d8a72621093db81
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-51240: Hochgeladene Datei fehlt bei der Registrierung über das Formular für die Unternehmensregistrierung

>[!NOTE]
>
>Dieser Patch wird durch [ACSD-55628](/help/support-tools/patches-available-in-qpt-tool/v1-1-42/acsd-55628-upload-file-company-registration-form-replace-file-customer-attribute-storefront.md) ersetzt.

Der Patch ACSD-51240 behebt das Problem, dass die hochgeladene Datei bei der Registrierung über das Registrierungsformular des Unternehmens fehlt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 installiert ist. Die Patch-ID ist ACSD-51240. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 &lt; 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Problem

Hochgeladene Datei fehlt bei der Registrierung über das Registrierungsformular für das Unternehmen.

<u>Zu reproduzierende Schritte</u>:

1. Legen Sie **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B >Company]** > **[!UICONTROL Enable]** = *Ja* fest.
1. Erstellen Sie ein neues Kundenattribut vom Typ **[!UICONTROL File]** , legen Sie **[!UICONTROL Show in StoreFront]** = *Ja* fest und wählen Sie **[!UICONTROL all forms]** aus.
1. Erstellen Sie ein neues Unternehmen in der Storefront und laden Sie ein Bild für das neue Attribut hoch.
Öffnen Sie das Unternehmen und den Administrator-Benutzer in der Storefront.

<u>Erwartete Ergebnisse</u>:

Die hochgeladene Datei wird angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die hochgeladene Datei wird weder auf der Firmenseite noch auf der Admin-Kundenseite im [!UICONTROL Commerce Admin] angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
