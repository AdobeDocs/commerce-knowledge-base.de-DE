---
title: 'ACSD-48404: *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* verursacht beim Drücken der Zurück-Taste des Browsers einen Fehler'
description: Wenden Sie den Patch ACSD-48404 an, um das Adobe Commerce-Problem zu beheben, bei dem *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* beim Drücken der Zurück-Taste des Browsers einen Fehler verursacht.
exl-id: b4b96198-dee6-4b3c-b60a-0983ef8ef7b2
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-48404: *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* verursacht einen Fehler beim Drücken der Zurück-Taste des Browsers

Der Patch ACSD-48404 behebt das Problem, bei dem *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* beim Drücken der Zurück-Taste des Browsers einen Fehler verursacht. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 installiert ist. Die Patch-ID lautet ACSD-48404. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.3 - p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

*[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* verursacht einen Fehler, wenn die Zurück-Taste des Browsers gedrückt wird.


<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]** und legen Sie die *[!UICONTROL Remember Category Pagination]* auf *Ja* fest.
1. Öffnen Sie eine Kategorie in der Storefront.
1. Wählen Sie einen Wert aus, der nicht der Standardwert in der Dropdown-Liste *[!UICONTROL Show Per Page]* ist. Nach Auswahl einer Option wird die Seite neu geladen.
1. Nachdem die Seite neu geladen wurde, klicken Sie auf ein beliebiges Produkt auf der Katalogseite.
1. Klicken Sie auf der geöffneten Produktdetailseite auf die Schaltfläche **[!UICONTROL Back]** des Browsers.

<u>Erwartete Ergebnisse</u>:

Die Katalogseite wird erneut geöffnet.

<u>Tatsächliche Ergebnisse</u>:

Die Kategorieseite gibt einen Fehler zurück.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
