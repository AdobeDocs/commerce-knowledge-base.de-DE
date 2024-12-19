---
title: 'ACSD-49706: Standardwert, der für das Attribut eines visuellen Farbfelds gespeichert wird, wenn kein Wert ausgewählt ist'
description: Wenden Sie den Patch ACSD-49706 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Standardwert für ein visuelles Musterattribut gespeichert wird, wenn kein Wert ausgewählt ist.
exl-id: fe6071df-f2a4-443a-acfa-67f3d253c5e4
feature: Admin Workspace, Attributes
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-49706: Standardwert, der für das Attribut eines visuellen Farbfelds gespeichert wird, wenn kein Wert ausgewählt ist

Mit dem Patch „ACSD-49706“ wird das Problem behoben, dass ein Standardwert für ein visuelles Farb-/Bildmuster-Attribut gespeichert wird, wenn kein Wert ausgewählt ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 installiert ist. Die Patch-ID ist ACSD-49706. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn kein Wert ausgewählt ist, wird ein Standardwert für ein visuelles Farbfeldattribut gespeichert.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. Klicken Sie auf **[!UICONTROL Add New Attribute]**.
1. Füllen Sie die Felder aus.

   * Wählen Sie beispielsweise den Eingabetyp *[!UICONTROL Visual Swatch]* und fügen Sie mehrere Optionen hinzu (z. B *„Rot*, *Grün*). Stellen Sie sicher, dass Sie eine dieser Optionen als Standard auswählen.
   * Klicken Sie auf **[!UICONTROL Save Attribute]**.

1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Bearbeiten Sie den *[!UICONTROL Default]* Attributsatz.
1. Verschieben Sie *[!UICONTROL New Attribute]* aus der *[!UICONTROL Unassigned Attributes]* in den *[!UICONTROL Product Details]* Ordner in der mittleren Spalte.

   * Klicken Sie auf **[!UICONTROL Save]**.

1. Erstellen Sie ein neues Produkt mit dem *[!UICONTROL Default]*.

   * Lassen Sie das *[!UICONTROL New Attribute]* leer und speichern Sie es.

1. Nach dem Speichern wird ein Wert in *[!UICONTROL New Attribute]* angezeigt.

<u>Erwartete Ergebnisse</u>:

*[!UICONTROL New Attribute]* ist standardmäßig kein Wert zugewiesen.

<u>Tatsächliche Ergebnisse</u>:

Beim Speichern eines Produkts wird ein Standardwert auf das Attribut angewendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
