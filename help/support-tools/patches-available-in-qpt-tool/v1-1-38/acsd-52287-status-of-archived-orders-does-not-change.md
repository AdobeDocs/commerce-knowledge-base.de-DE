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

Der Patch ACSD-52287 behebt das Problem, dass der Status archivierter Bestellungen sich nicht von *completed* nach *geschlossen* nach der Übermittlung des Kreditprotokolls in das Raster eintragen. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 installiert ist. Die Patch-ID ist ACSD-52287. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Status archivierter Bestellungen ändert sich nicht von *completed* nach *geschlossen* nach der Übermittlung des Kreditprotokolls in das Raster eintragen.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren *[!UICONTROL Asynchronous Indexing]*.
   * Navigieren Sie in der Admin-Seitenleiste zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * Erweitern Sie im linken Bereich den **[!UICONTROL Advanced]** auswählen **[!UICONTROL Developer]** darunter.
   * Erweitern Sie die **[!UICONTROL Grid Settings]** Abschnitt.
   * Satz *[!UICONTROL Asynchronous indexing]* nach *Ja*.
   * Klicks **[!UICONTROL Save Config]**.
1. Konfigurieren Sie die *[!UICONTROL Order Archive]*.
   * Navigieren Sie in der Admin-Seitenleiste zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * Erweitern Sie im linken Bereich den **[!UICONTROL Sales]** auswählen **[!UICONTROL Sales]** darunter.
   * Erweitern Sie die **[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]** Abschnitt.
   * Satz *[!UICONTROL Enable Archiving]* nach *Ja* (Belassen Sie die restlichen Konfigurationen als Standard.)
   * Klicks **[!UICONTROL Save Config]**.
1. Platzieren Sie eine Bestellung im Frontend.
1. Führen Sie die [!DNL cron]  , damit die Reihenfolge in der *[!UICONTROL Admin Order Grid]*.
1. Rechnungsstellung und Versand der Bestellung zur Aktualisierung des Bestellstatus auf *Fertig*.
1. Führen Sie die [!DNL cron]  , um die *[!UICONTROL Sales Order Grid]* mit dem neuesten Bestellstatus.
1. Archivieren Sie die Bestellung.
1. Navigieren Sie zu *[!UICONTROL Archived order grid]*.
1. Öffnen Sie die archivierte Bestellung und erstatten Sie die Bestellung offline, indem Sie eine [!UICONTROL Credit Memo] , um [!UICONTROL Order status]: *Geschlossen*.
1. Führen Sie die [!DNL cron] für einige Male.
1. Überprüfen Sie die *[!UICONTROL Archived order grid]* für den neuen Bestellstatus.

<u>Erwartete Ergebnisse</u>:

Die Reihenfolge wird als *Geschlossen*.

<u>Tatsächliche Ergebnisse</u>:

Die Reihenfolge wird als *Fertig*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
