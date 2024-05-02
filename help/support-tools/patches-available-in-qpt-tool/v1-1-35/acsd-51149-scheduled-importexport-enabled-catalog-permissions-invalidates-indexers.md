---
title: '"ACSD-51149: Geplant [!UICONTROL ImportExport] mit aktivierten [!UICONTROL Catalog Permissions] invalidiert indexers'''
description: Wenden Sie den Patch ACSD-51149 an, um das Adobe Commerce-Leistungsproblem zu beheben, bei dem die geplante [!UICONTROL ImportExport] mit aktivierten [!UICONTROL Catalog Permissions] Invalidiert Indexer.
feature: Cache, Data Import/Export
role: Admin
exl-id: 3a26f4be-8e52-407d-bb25-2841458f3aa5
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-51149: Geplant [!UICONTROL ImportExport] mit aktivierten [!UICONTROL Catalog Permissions] Invalidierungen von Indexern

Der Patch ACSD-51149 behebt das Problem, bei dem der geplante [!UICONTROL ImportExport] mit aktivierten [!UICONTROL Catalog Permissions] Invalidiert Indexer. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-51149. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Geplant [!UICONTROL ImportExport] mit aktivierten [!UICONTROL Catalog Permissions] Invalidiert Indexer.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren *[!UICONTROL Catalog Permissions]*.
1. Setzen Sie alle Indexer auf *[!UICONTROL Update by Schedule]*.
1. Erstellen Sie ein einfaches Produkt.
1. Diese Ware exportieren über **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**.
1. Laden Sie die exportierte CSV-Datei herunter und legen Sie sie in `<AC root folder>/var/import`.
1. Erstellen Sie einen geplanten Produktimport mit der heruntergeladenen CSV-Datei.
1. Führen Sie die vollständige Neuindizierung aus.
1. Überprüfen Sie den Indexstatus. Alle Indexer sollten in *[!UICONTROL Ready]* -Status.
1. Führen Sie den erstellten geplanten Import aus dem Raster aus.
1. Überprüfen Sie den Indexstatus erneut.

<u>Erwartete Ergebnisse</u>:

Alle Indexer befinden sich im *[!UICONTROL Ready]* -Status.

<u>Tatsächliche Ergebnisse</u>:

Einige Indexer befinden sich in *[!UICONTROL Reindex Required]* -Status.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
