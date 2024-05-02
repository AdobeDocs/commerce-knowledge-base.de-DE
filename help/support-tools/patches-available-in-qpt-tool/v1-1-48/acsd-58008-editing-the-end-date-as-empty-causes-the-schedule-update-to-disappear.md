---
title: '"ACSD-58008: Wird das Enddatum als "leer"geändert, wird der Zeitplan-Update nicht mehr angezeigt."'
description: Wenden Sie den Patch ACSD-58008 an, um das Adobe Commerce-Problem zu beheben, bei dem das Bearbeiten des Enddatums als *leer* dazu führt, dass die Zeitplanaktualisierung verschwindet.
feature: Staging, Page Content
role: Admin, Developer
source-git-commit: 174ed3b35edeb26b09b04bc7d88111a5719e08f8
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-58008: Enddatum bearbeiten als *leer* führt dazu, dass das Planupdate verschwindet

Der Patch ACSD-58008 behebt das Problem, bei dem das Enddatum als *leer* führt dazu, dass die Zeitplanaktualisierung verschwindet. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 ist installiert. Die Patch-ID ist ACSD-58008. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Bearbeiten des Enddatums als *leer* führt dazu, dass das Planupdate verschwindet

<u>Zu reproduzierende Schritte</u>:

1. Anmelden als [!UICONTROL Admin].
1. Navigieren Sie zu **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** und erstellen Sie eine Seite.
1. Wählen Sie die erstellte Seite aus und klicken Sie auf **[!UICONTROL Schedule New Update]**. *(In der oberen rechten Ecke der Seite navigieren)*.
1. Erstellen Sie vier Updates. *(z. B. als Inkrement von* 2 *Minuten)*.
1. Aktualisieren Sie die *Update 2* und ändern Sie die Zeit auf eine Zeit, die der letzten *Update 4*.
1. Speichern Sie die vorgenommenen Aktualisierungen.

<u>Erwartete Ergebnisse</u>:

Die Aktualisierung des Zeitplans zeigt die *Update 3*.

<u>Tatsächliche Ergebnisse</u>:

Die Zeitplanaktualisierung zeigt nicht die *Update 3*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.