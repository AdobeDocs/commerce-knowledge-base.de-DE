---
title: 'ACSD-52219: Problem mit Admin-Raster-Filtern beim Wechseln der Lesezeichenansicht behoben'
description: Wenden Sie den Patch ACSD-52219 an, um das Adobe Commerce-Problem zu beheben, bei dem die gespeicherten Filter der Admin-Raster nicht wie erwartet funktionieren, wenn häufig zwischen Lesezeichenansichten gewechselt wird.
feature: Admin Workspace
role: Admin
exl-id: e8333ee7-28a8-4457-aeff-6828f8ca9412
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-52219: Problem mit Admin-Raster-Filtern beim Wechseln der Lesezeichenansicht behoben

Der Patch ACSD-52219 behebt das Problem, dass die gespeicherten Filter der Admin-Raster beim häufigen Wechseln zwischen Lesezeichenansichten nicht wie erwartet funktionieren. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39 installiert ist. Die Patch-ID ist ACSD-52219. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn häufig zwischen Lesezeichenansichten gewechselt wird, funktionieren die gespeicherten Filter in den Admin Rastern nicht wie gewünscht.

<u>Zu reproduzierende Schritte</u>:

1. Rufen Sie das Raster [!DNL Sales Order] im Admin auf.
1. Erstellen Sie zwei bis drei Filter.
1. Überprüfen Sie die Filtereinstellungen, indem Sie die Ansichten wechseln, um sicherzustellen, dass sie korrekt gespeichert werden.
1. Navigieren Sie zu Filter1 oder Filter2.
1. Aktualisieren Sie die Seite, um die angezeigten Daten zu aktualisieren.
1. Wechseln Sie zu einer anderen Ansicht und beachten Sie, dass die Filter unverändert bleiben.
1. Beachten Sie, dass in der Standardansicht jetzt gefilterte Ergebnisse angezeigt werden, auch wenn kein spezifischer Filter dafür festgelegt wurde.

<u>Erwartete Ergebnisse</u>:

Die Filter werden nicht verändert und behalten ihren ursprünglichen Status bei.

<u>Tatsächliche Ergebnisse</u>:

Beim Ändern einer Ansicht werden die Filter vermischt und die richtige Ansicht wird nicht gespeichert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
