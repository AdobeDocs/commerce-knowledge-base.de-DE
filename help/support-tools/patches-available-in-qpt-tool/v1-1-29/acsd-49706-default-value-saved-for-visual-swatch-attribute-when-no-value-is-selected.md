---
title: "ACSD-49706: Standardwert, der für das Attribut für visuelle Muster gespeichert wird, wenn kein Wert ausgewählt ist"
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

Der Patch ACSD-49706 behebt das Problem, dass ein Standardwert für ein visuelles Farbfeldattribut gespeichert wird, wenn kein Wert ausgewählt ist. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 ist installiert. Die Patch-ID ist ACSD-49706. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn kein Wert ausgewählt ist, wird für ein visuelles Farbfeldattribut ein Standardwert gespeichert.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. Klicks **[!UICONTROL Add New Attribute]**.
1. Füllen Sie die Felder aus.

   * Wählen Sie beispielsweise den Eingabetyp *[!UICONTROL Visual Swatch]* und fügen Sie mehrere Optionen hinzu (z. B. *Rot*, *Grün*). Stellen Sie sicher, dass Sie eine dieser Optionen als Standard auswählen.
   * Klicks **[!UICONTROL Save Attribute]**.

1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Bearbeiten Sie die *[!UICONTROL Default]* -Attributsatz.
1. Verschieben *[!UICONTROL New Attribute]* aus der Spalte *[!UICONTROL Unassigned Attributes]* der *[!UICONTROL Product Details]* in der mittleren Spalte.

   * Klicks **[!UICONTROL Save]**.

1. Erstellen Sie ein neues Produkt mit dem *[!UICONTROL Default]* -Attributsatz.

   * Lassen Sie die *[!UICONTROL New Attribute]* leer lassen und speichern.

1. Nach dem Speichern wird ein Wert in *[!UICONTROL New Attribute]*.

<u>Erwartete Ergebnisse</u>:

Es wird kein Wert zugewiesen für *[!UICONTROL New Attribute]* Standardmäßig.

<u>Tatsächliche Ergebnisse</u>:

Beim Speichern eines Produkts wird auf das Attribut ein Standardwert angewendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
