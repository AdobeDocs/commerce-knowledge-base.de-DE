---
title: '"ACSD-52095: Lagerwert verwalten ist beim Exportieren von CSV falsch'
description: Wenden Sie den Patch ACSD-52095 an, um das Adobe Commerce-Problem zu beheben, bei dem der Lagerwert für das Produktmanagement beim Exportieren von CSV falsch ist.
feature: Inventory, Products
role: Admin, Developer
exl-id: 9e599931-e9b1-4216-b78d-3993d9c3132d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-52095: [!UICONTROL Manage Stock] Wert beim Exportieren von CSV falsch

Der Patch ACSD-52095 behebt das Problem, bei dem das Produkt `manage_stock` beim Exportieren von CSV falsch ist. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-52095. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die `manage_stock` in der CSV-Datei nach dem Produktexport fälschlicherweise auf 0 gesetzt.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** und **[!UICONTROL Manage Stock]** = *[!UICONTROL No]*.
1. Erstellen und speichern Sie ein neues Produkt.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Export]**.
1. Auswählen *[!UICONTROL Entity Type]* = *[!UICONTROL Products]* und die Erzeugnisse ausführen.
1. Überprüfen Sie die generierte CSV-Datei: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Gehen Sie erneut zu **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** und legen  **[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]*.
1. Navigieren Sie zu **System** > **Export**.
Auswählen *[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]*.
1. Überprüfen Sie die generierte CSV-Datei: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Öffnen Sie das Produkt in der Admin-Konsole, navigieren Sie zu **[!UICONTROL Advanced Inventory]** und überprüfen Sie die **[!UICONTROL Manage Stock]** -Wert.

<u>Erwartete Ergebnisse</u>

Die **[!UICONTROL Manage Stock]** Wert ist *1* wenn sie für die Produkte aktiviert ist.

<u>Tatsächliche Ergebnisse</u>

Die **[!UICONTROL Manage Stock]** Wert ist *0* wenn sie für die Produkte aktiviert ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] Handbuch.
