---
title: 'ACSD-57565: Im Bestellungs-Dashboard werden falsche Bestellinformationen angezeigt'
description: Wenden Sie den Patch ACSD-57565 an, um das Problem in Adobe Commerce zu beheben, bei dem im Bestell-Dashboard falsche Bestellinformationen angezeigt werden, bis der Zeitraum aktualisiert wird.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 5b292fef-23f6-479f-bf76-adad53d30cf4
source-git-commit: fdf6e6e85f903a26a7b44674937ccf88ee769d06
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-57565: Im Bestellungs-Dashboard werden falsche Bestellinformationen angezeigt

Mit dem Patch ACSD-57565 wird das Problem behoben, dass im Bestellungs-Dashboard falsche Bestellinformationen angezeigt werden, bis der Zeitraum aktualisiert wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.48 installiert ist. Die Patch-ID ist ACSD-57565. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden

## Problem

Im Bestell-Dashboard werden falsche Bestellinformationen angezeigt.

<u>Schritte zur Reproduktion</u>:

1. **[!UICONTROL dashboard charts]** aktivieren.
1. Bestellung erstellen und fakturieren.
1. Warten Sie nach der Bestellerstellung mindestens 24 Stunden.
1. Überprüfen Sie die **[!UICONTROL dashboard chart]**.
1. Notieren Sie sich die vollständige Bestellanzahl.
1. Ändern Sie die Zeit in *aktuellen Monat* und ändern Sie sie dann wieder zurück in *Heute*.

<u>Erwartete Ergebnisse</u>:

Das Dashboard-Diagramm sollte stets die richtigen Statistiken anzeigen.

<u>Tatsächliche Ergebnisse</u>:

Das Dashboard-Diagramm zeigt falsche Statistiken beim ersten Laden an. Die genauen Statistiken des Diagramms werden nach dem Zeitraum aktualisiert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
