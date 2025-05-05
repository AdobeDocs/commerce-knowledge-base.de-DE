---
title: 'MDVA-37364: Benutzerdefiniertes Kundenattribut des Datentyps unterbricht die Rasterbenutzeroberfläche'
description: Der Patch MDVA-37364 löst das Problem, dass das benutzerdefinierte Kundenattribut vom Datentyp die Benutzeroberfläche des Kundenrasters beschädigt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-37364. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce Version 2.4.4 behoben wird.
exl-id: d25baabf-45eb-403c-9f88-9c2448cc7b49
feature: Attributes, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37364: Benutzerdefiniertes Kundenattribut des Datentyps unterbricht die Rasterbenutzeroberfläche

Der Patch MDVA-37364 löst das Problem, dass das benutzerdefinierte Kundenattribut vom Datentyp die Benutzeroberfläche des Kundenrasters beschädigt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-37364. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce Version 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0-2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim benutzerdefinierten Kundenattribut des Datentyps ist die Benutzeroberfläche des Kundenrasters nicht mehr verfügbar.

<u>Schritte zur Reproduktion</u>:

1. Benutzerdefiniertes Attribut mit Datentyp erstellen:
   * Navigieren Sie **Stores** > **Attribute** > **Attribut hinzufügen**.
   * Legen Sie den Eingabetyp auf „Datum“ fest.
   * Legen Sie die Option Zu Spaltenoptionen hinzufügen auf Ja fest.
   * Speichern Sie das Attribut.
1. Navigieren Sie **Admin** > **Kunden** > **Alle Kunden**.
   * Fügen Sie das neu hinzugefügte benutzerdefinierte Attribut dem Raster aus der Option Spalten hinzu.
1. Erstellen/Bearbeiten eines Kunden und Festlegen des Werts des erstellten benutzerdefinierten Datumsattributfelds.
1. Speichern, neu indizieren und den Cache löschen.
1. Navigieren Sie **Kunden** > **Alle Kunden**.
   * Überprüfen Sie das Kundenraster.

<u>Erwartete Ergebnisse</u>:

Das Admin-Kundenraster zeigt alle Daten an, einschließlich des neuen benutzerdefinierten Datumsattributs, ohne dass die Benutzeroberfläche des Kundenrasters beschädigt wird.

<u>Tatsächliche Ergebnisse</u>:

Die Admin-Benutzeroberfläche für Kundenraster ist fehlerhaft.

## Patch anwenden

Verwenden Sie je nach Bereitstellungstyp die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Überprüfen Sie mit dem Quality Patches Tool, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
