---
title: 'ACSD-49898: Das Produktraster löst eine Ausnahme aus'
description: Wenden Sie den Patch ACSD-49898 an, um das Adobe Commerce-Problem zu beheben, bei dem das Produktraster eine Ausnahme auslöst, wenn ein gebündeltes Produkt einen Sonderpreis von über 1.000 aufweist.
exl-id: 16a0ec90-7577-46ef-aeb3-a7e9658cf64b
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-49898: Das Produktraster löst eine Ausnahme aus

Mit dem Patch ACSD-49898 wird das Problem behoben, dass das Produktraster eine Ausnahme ausgibt, wenn ein gebündeltes Produkt einen Sonderpreis von mehr als 1.000 aufweist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 installiert ist. Die Patch-ID ist ACSD-49898. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Produktraster löst eine Ausnahme aus, wenn ein gebündeltes Produkt einen Sonderpreis von mehr als 1.000 aufweist. Das Problem betrifft die Verwendung von Kommas anstelle von Punkten für Dezimalzahlen in bestimmten Gebietsschemata.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein gebündeltes Produkt.
1. Setzen Sie den Sonderpreis auf 9999; Speichern und schließen.
1. Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]**

>[!NOTE]
>
>Suchen Sie nach der gebündelten Produkt-SKU, wenn sie nicht sichtbar ist.

<u>Erwartete Ergebnisse</u>:

* Der Benutzer kann das gebündelte Produkt mit dem Sonderpreis filtern/anzeigen.
* Der Sonderpreis wird als Prozentsatz für gebündelte Produkte und als Preis für andere Produktarten angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Folgender Fehler wird ausgegeben: *Nicht-numerischer Wert gefunden*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
