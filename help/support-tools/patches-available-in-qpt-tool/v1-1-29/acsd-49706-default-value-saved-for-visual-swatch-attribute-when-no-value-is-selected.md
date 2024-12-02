---
title: 'ACSD-49706: Standardwert, der für das visuelle Farbfeldattribut gespeichert wird, wenn kein Wert ausgewählt ist'
description: Wenden Sie den Patch ACSD-49706 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Standardwert für ein visuelles Farbfeldattribut gespeichert wird, wenn kein Wert ausgewählt ist.
exl-id: fe6071df-f2a4-443a-acfa-67f3d253c5e4
feature: Admin Workspace, Attributes
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-49706: Standardwert, der für das visuelle Farbfeldattribut gespeichert wird, wenn kein Wert ausgewählt ist

Der Patch ACSD-49706 behebt das Problem, dass ein Standardwert für ein visuelles Farbfeldattribut gespeichert wird, wenn kein Wert ausgewählt ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 installiert ist. Die Patch-ID ist ACSD-49706. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn kein Wert ausgewählt ist, wird für ein visuelles Farbfeldattribut ein Standardwert gespeichert.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. Klicken Sie auf **[!UICONTROL Add New Attribute]**.
1. Füllen Sie die Felder aus.

   * Wählen Sie beispielsweise den Eingabetyp &quot;*[!UICONTROL Visual Swatch]*&quot;und fügen Sie mehrere Optionen hinzu (z. B. *Rot*, *Grün*). Stellen Sie sicher, dass Sie eine dieser Optionen als Standard auswählen.
   * Klicken Sie auf **[!UICONTROL Save Attribute]**.

1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Bearbeiten Sie den Attributsatz *[!UICONTROL Default]* .
1. Verschieben Sie *[!UICONTROL New Attribute]* aus der Spalte *[!UICONTROL Unassigned Attributes]* in den Ordner *[!UICONTROL Product Details]* in der mittleren Spalte.

   * Klicken Sie auf **[!UICONTROL Save]**.

1. Erstellen Sie ein neues Produkt mit dem Attributsatz *[!UICONTROL Default]* .

   * Lassen Sie die *[!UICONTROL New Attribute]* leer und speichern Sie sie.

1. Nach dem Speichern wird ein Wert in *[!UICONTROL New Attribute]* angezeigt.

<u>Erwartete Ergebnisse</u>:

*[!UICONTROL New Attribute]* wird standardmäßig kein Wert zugewiesen.

<u>Tatsächliche Ergebnisse</u>:

Beim Speichern eines Produkts wird auf das Attribut ein Standardwert angewendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
