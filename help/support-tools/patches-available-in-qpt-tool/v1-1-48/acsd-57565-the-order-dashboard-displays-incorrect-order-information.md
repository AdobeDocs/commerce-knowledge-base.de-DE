---
title: 'ACSD-57565: Das Dashboard für die Bestellung zeigt falsche Bestellinformationen an.'
description: Wenden Sie den Patch ACSD-57565 an, um das Adobe Commerce-Problem zu beheben, bei dem das Bestell-Dashboard falsche Bestellinformationen anzeigt, bis der Zeitraum aktualisiert wurde.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 5b292fef-23f6-479f-bf76-adad53d30cf4
source-git-commit: fdf6e6e85f903a26a7b44674937ccf88ee769d06
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-57565: Das Dashboard für Bestellungen zeigt falsche Bestellinformationen an

Der Patch ACSD-57565 behebt das Problem, dass das Bestell-Dashboard falsche Bestellinformationen anzeigt, bis der Zeitraum aktualisiert wurde. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.48 ist installiert. Die Patch-ID ist ACSD-57565. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden der Patch-ID als Suchschlüsselwort, um den Patch zu finden

## Problem

Im Dashboard für Bestellungen werden falsche Bestellinformationen angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren **[!UICONTROL dashboard charts]**.
1. Erstellen Sie eine Bestellung und rechnen Sie sie aus.
1. Warten Sie mindestens 24 Stunden nach der Erstellung der Bestellung.
1. Überprüfen Sie die **[!UICONTROL dashboard chart]** Daten.
1. Notieren Sie sich die vollständige Bestellanzahl.
1. Ändern Sie die Zeit in *Aktueller Monat*, und ändern Sie sie dann zurück zu *heute*.

<u>Erwartete Ergebnisse</u>:

Das Dashboard-Diagramm sollte stets die korrekten Statistiken anzeigen.

<u>Tatsächliche Ergebnisse</u>:

Das Dashboard-Diagramm zeigt beim ersten Laden falsche Statistiken an. Die genauen Statistiken der Grafik werden nach dem Zeitraum aktualisiert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
