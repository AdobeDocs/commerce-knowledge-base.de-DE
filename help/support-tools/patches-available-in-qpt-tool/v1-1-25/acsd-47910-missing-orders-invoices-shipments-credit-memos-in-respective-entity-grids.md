---
title: "ACSD-47910: fehlende Bestellungen, Rechnungen, Sendungen, Kreditkarten in den jeweiligen Unternehmensnetzen"
description: Wenden Sie den Patch ACSD-47910 an, um das Adobe Commerce-Problem zu beheben, das bei fehlenden Bestellungen, Rechnungen, Sendungen und Kreditkarten in den jeweiligen Entitätsrasten auftritt.
exl-id: 4eb897ec-16e4-420e-89a6-c8f7c8740303
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-47910: fehlende Bestellungen, Rechnungen, Sendungen und Kreditkarten in den jeweiligen Unternehmensnetzen

Der Patch ACSD-47910 behebt das Problem, bei dem es fehlende Bestellungen, Rechnungen, Sendungen und Kreditkarten in den jeweiligen Entitätsrasten gibt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 installiert ist. Die Patch-ID lautet ACSD-47910. Die Version, in der dieses Problem behoben wird, ist noch nicht verfügbar.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Fehlende Bestellungen, Rechnungen, Sendungen und Kreditkarten in den jeweiligen Unternehmensrasten.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie **[!UICONTROL Asynchronous indexing]** bei **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]**.
1. Bestellen Sie zwei Bestellungen.
1. Führen Sie den Cron aus, um diese Bestellungen mit dem Raster zu synchronisieren.
1. Öffnen Sie eine der Bestellungen und machen Sie sie bereit zur Fakturierung. SENDEN SIE DIE RECHNUNG NOCH NICHT.
1. Machen Sie eine neue Bestellung fertig, um sie an der Frontend platzieren zu können. KLICKEN SIE NOCH NICHT AUF DIE SCHALTFLÄCHE PLATZIERUNG .
1. Fügen Sie eine `sleep(30)` im `foreach` bei `NotSyncedDataProvider::L43` hinzu.
1. Führen Sie `bin/magento cron:run` aus.
1. Jetzt bestellen Sie die neue Bestellung.
1. Rechnungsstellung der vorherigen Bestellung.
1. Führen Sie den Cron erneut aus, damit die neue Bestellung synchronisiert wird.
1. Navigieren Sie zum Bestellraster in der Admin-Konsole.

<u>Erwartete Ergebnisse</u>:

Die neue Reihenfolge sollte im Bestellraster angezeigt werden.

<u>Tatsächliche Ergebnisse</u>:

Die vorherige Bestellaktualisierung wurde mit dem Raster (**[!UICONTROL status: Processing]**) synchronisiert. Die neue Reihenfolge wird nie im Raster angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
