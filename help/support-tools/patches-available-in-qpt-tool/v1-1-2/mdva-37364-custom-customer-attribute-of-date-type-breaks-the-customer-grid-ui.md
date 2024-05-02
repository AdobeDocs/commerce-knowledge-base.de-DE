---
title: "MDVA-37364: Benutzerdefiniertes Kundenattribut des Datumstyps bricht die Rasterbenutzeroberfläche aus"
description: Der Patch MDVA-37364 behebt das Problem, dass das benutzerdefinierte Kundenattribut des Datumstyps die Benutzeroberfläche des Kundenrasters beschädigt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-37364. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.4 behoben werden soll.
exl-id: d25baabf-45eb-403c-9f88-9c2448cc7b49
feature: Attributes, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37364: Benutzerdefiniertes Kundenattribut des Datumstyps bricht die Raster-Benutzeroberfläche aus

Der Patch MDVA-37364 behebt das Problem, dass das benutzerdefinierte Kundenattribut des Datumstyps die Benutzeroberfläche des Kundenrasters beschädigt. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 ist installiert. Die Patch-ID lautet MDVA-37364. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.4 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0-2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzerdefiniertes Kundenattribut des Datumstyps beschädigt die Benutzeroberfläche des Kundenrasters.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein benutzerdefiniertes Attribut mit Datentyp:
   * Navigieren Sie zu **Stores** > **Attribute** > **Attribut hinzufügen**.
   * Legen Sie den Eingabetyp auf Datum fest.
   * Setzen Sie die Option Zu Spaltenoptionen hinzufügen auf Ja.
   * Speichern Sie das Attribut.
1. Navigieren Sie zu **Admin** > **Kunden** > **Alle Kunden**.
   * Fügen Sie das neu hinzugefügte benutzerdefinierte Attribut über die Spaltenoption zum Raster hinzu.
1. Erstellen/bearbeiten Sie einen Kunden und legen Sie den Wert des erstellten benutzerdefinierten Datumsattributfelds fest.
1. Speichern, Neuindizieren und leeren Sie den Cache.
1. Navigieren Sie zu **Kunden** > **Alle Kunden**.
   * Überprüfen Sie das Kundenraster.

<u>Erwartete Ergebnisse</u>:

Das Admin-Kundenraster zeigt alle Daten einschließlich des neuen benutzerdefinierten Datumsattributs an, ohne dass die Kundenraster-Benutzeroberfläche beschädigt wird.

<u>Tatsächliche Ergebnisse</u>:

Die Administrator-Benutzeroberfläche für das Kundenraster ist fehlerhaft.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungstyp die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) Abschnitt.
