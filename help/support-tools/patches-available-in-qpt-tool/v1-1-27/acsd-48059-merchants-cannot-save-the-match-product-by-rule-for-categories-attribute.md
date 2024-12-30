---
title: 'ACSD-48059: Händler können keine [!UICONTROL Match product by rule] für das Kategorienattribut speichern.'
description: Wenden Sie den Patch ACSD-48059 an, um das Adobe Commerce-Problem zu beheben, bei dem Händler die [!UICONTROL Match product by rule] für das Kategorieattribut nicht speichern können.
exl-id: 97213157-1b54-4634-9c76-c9ab8fa96e17
feature: Admin Workspace, Attributes, Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-48059: Händler können die *[!UICONTROL Match product by rule]* für das Kategorieattribut nicht speichern

Mit dem Patch ACSD-48059 wird das Problem behoben, dass Händler die *[!UICONTROL Match product by rule]* für das Kategorieattribut in [!DNL Visual Merchandiser] nicht speichern können. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 installiert ist. Die Patch-ID ist ACSD-48059. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) >=2.3.7 &lt;2.4.7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Händler können die *[!UICONTROL Match product by rule]* für das Kategorieattribut in [!DNL Visual Merchandiser] nicht speichern.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Visual Merchandiser]** > **[!UICONTROL Visible Attributes for Category Rules]** und fügen Sie Kategorien hinzu.
1. Navigieren Sie zu Adobe Commerce Admin > **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
   * Navigieren Sie zum Abschnitt [!UICONTROL Products in Category] .
   * Fügen Sie eine neue *[!UICONTROL Match products by rule]* mit dem Attribut categories hinzu.

<u>Erwartete Ergebnisse</u>:

Die Kategorie wurde gespeichert.

<u>Tatsächliche Ergebnisse</u>:

* Sie können die Kategorie mit der neuen Regel und Bedingung nicht speichern.
* *Beim Speichern der Kategorie ist ein Fehler*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
