---
title: 'ACSD-58008: Wenn Sie das Enddatum als "leer"ändern, wird das Zeitplan-Update nicht mehr angezeigt.'
description: Wenden Sie den Patch ACSD-58008 an, um das Adobe Commerce-Problem zu beheben, bei dem das Bearbeiten des Enddatums als *leer* dazu führt, dass die Zeitplanaktualisierung verschwindet.
feature: Staging, Page Content
role: Admin, Developer
exl-id: bfa590b8-377b-49dd-9aff-f89b8fd815c4
source-git-commit: d7ace1f20defb01105d4a241f971b06fca052215
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-58008: Wenn Sie das Enddatum als *leer* ändern, wird das Zeitplan-Update nicht mehr angezeigt

Der Patch ACSD-58008 behebt das Problem, bei dem das Bearbeiten des Enddatums als *leer* dazu führt, dass das Planaktualisierung verschwindet. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 installiert ist. Die Patch-ID ist ACSD-58008. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Durch Bearbeiten des Enddatums als *leer* wird die Zeitplanaktualisierung ausgeblendet

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich als [!UICONTROL Admin] an.
1. Gehen Sie zu **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** und erstellen Sie eine Seite.
1. Wählen Sie die erstellte Seite aus und klicken Sie auf **[!UICONTROL Schedule New Update]**. *(Navigieren Sie dazu oben rechts auf der Seite)*.
1. Erstellen Sie vier Updates. *(z. B. als Erhöhung von* 2 *Minuten)*.
1. Aktualisieren Sie die *Aktualisierung 2* und ändern Sie die Zeit in einen Zeitpunkt, der vor dem letzten *Update 4* liegt.
1. Speichern Sie die vorgenommenen Aktualisierungen.

<u>Erwartete Ergebnisse</u>:

Das Planaktualisierung zeigt die *Aktualisierung 3* an.

<u>Tatsächliche Ergebnisse</u>:

In der Zeitplanaktualisierung wird die *Aktualisierung 3* nicht angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
