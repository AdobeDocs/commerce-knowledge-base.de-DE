---
title: 'ACSD-52095: Lagerwert verwalten ist beim Exportieren von CSV falsch'
description: Wenden Sie den Patch ACSD-52095 an, um das Adobe Commerce-Problem zu beheben, bei dem der Lagerwert für das Produktmanagement beim Exportieren von CSV falsch ist.
feature: Inventory, Products
role: Admin, Developer
exl-id: 9e599931-e9b1-4216-b78d-3993d9c3132d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-52095: [!UICONTROL Manage Stock] Wert beim Exportieren von CSV ist falsch

Der Patch ACSD-52095 behebt das Problem, dass der Produkt-Wert `manage_stock` beim Exportieren von CSV falsch ist. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-52095. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Wert `manage_stock` wird in der CSV-Datei nach dem Produktexport fälschlicherweise auf 0 gesetzt.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** und legen Sie **[!UICONTROL Manage Stock]** = *[!UICONTROL No]* fest.
1. Erstellen und speichern Sie ein neues Produkt.
1. Gehen Sie zu **[!UICONTROL System]** > **[!UICONTROL Export]**.
1. Wählen Sie *[!UICONTROL Entity Type]* = *[!UICONTROL Products]* aus und exportieren Sie die Produkte.
1. Überprüfen Sie die generierte CSV-Datei: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Gehen Sie erneut zu **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** und legen Sie **[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]* fest.
1. Wechseln Sie zu **System** > **Export**.
Wählen Sie *[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]* aus.
1. Überprüfen Sie die generierte CSV-Datei: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Öffnen Sie das Produkt in der Admin-Konsole, wechseln Sie zu &quot;**[!UICONTROL Advanced Inventory]**&quot;und überprüfen Sie den Wert &quot;**[!UICONTROL Manage Stock]**&quot;.

<u>Erwartete Ergebnisse</u>

Der **[!UICONTROL Manage Stock]** -Wert ist *1*, wenn er für die Produkte aktiviert ist.

<u>Tatsächliche Ergebnisse</u>

Der **[!UICONTROL Manage Stock]** -Wert ist *0* , wenn er für die Produkte aktiviert ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] -Handbuch.
