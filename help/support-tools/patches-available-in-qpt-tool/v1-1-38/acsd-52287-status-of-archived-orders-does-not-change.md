---
title: "ACSD-52287: Status archivierter Bestellungen ändert sich nicht"
description: Wenden Sie den Patch ACSD-52287 an, um das Adobe Commerce-Problem zu beheben, bei dem sich der Status archivierter Bestellungen nach dem Senden des Kreditprotokolls nicht von *abgeschlossen* auf *geschlossen* im Raster ändert.
feature: Orders, Checkout
role: Admin, Developer
exl-id: c88c5c87-eec7-4105-9e4e-815d0888a34b
source-git-commit: 178023177975f210ebf7dd07e8c75cfe3ac89ff1
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-52287: Status archivierter Bestellungen ändert sich nicht

Der Patch ACSD-52287 behebt das Problem, dass der Status archivierter Bestellungen sich nach dem Senden des Kreditprotokolls nicht von *completed* in *closed* im Raster ändert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 installiert ist. Die Patch-ID ist ACSD-52287. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Status archivierter Bestellungen ändert sich nicht von *completed* in *closed* im Raster, nachdem das Kreditmemo übermittelt wurde.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie *[!UICONTROL Asynchronous Indexing]*.
   * Wechseln Sie in der Admin-Seitenleiste zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * Erweitern Sie im linken Bereich den Abschnitt **[!UICONTROL Advanced]** und wählen Sie unter &quot;**[!UICONTROL Developer]**&quot;.
   * Erweitern Sie den Abschnitt **[!UICONTROL Grid Settings]** .
   * Setzen Sie *[!UICONTROL Asynchronous indexing]* auf *Ja*.
   * Klicken Sie auf **[!UICONTROL Save Config]**.
1. Konfigurieren Sie die *[!UICONTROL Order Archive]*.
   * Wechseln Sie in der Admin-Seitenleiste zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * Erweitern Sie im linken Bereich den Abschnitt **[!UICONTROL Sales]** und wählen Sie unter &quot;**[!UICONTROL Sales]**&quot;.
   * Erweitern Sie den Abschnitt **[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]** .
   * Setzen Sie *[!UICONTROL Enable Archiving]* auf *Ja* (Belassen Sie die restlichen Konfigurationen als Standard).
   * Klicken Sie auf **[!UICONTROL Save Config]**.
1. Platzieren Sie eine Bestellung im Frontend.
1. Führen Sie die [!DNL cron] aus, damit die Reihenfolge in der *[!UICONTROL Admin Order Grid]* angezeigt wird.
1. Rechnung und Versand der Bestellung, um den Bestellstatus auf *Abgeschlossen* zu aktualisieren.
1. Führen Sie die [!DNL cron] aus, um den *[!UICONTROL Sales Order Grid]* mit dem neuesten Bestellstatus zu aktualisieren.
1. Archivieren Sie die Bestellung.
1. Wechseln Sie zu &quot;*[!UICONTROL Archived order grid]*&quot;.
1. Öffnen Sie die archivierte Bestellung und geben Sie die Bestellung offline zurück, indem Sie eine [!UICONTROL Credit Memo] erstellen, um die [!UICONTROL Order status]: *Geschlossen* zu machen.
1. Führen Sie die [!DNL cron] einige Male aus.
1. Überprüfen Sie die *[!UICONTROL Archived order grid]* auf den neuen Bestellstatus.

<u>Erwartete Ergebnisse</u>:

Die Reihenfolge wird als *Geschlossen* angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die Reihenfolge wird als *Abgeschlossen* angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
