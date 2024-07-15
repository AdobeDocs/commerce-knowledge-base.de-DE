---
title: "MCP-87 Adobe Commerce Patch: Storefront defekt"
description: Der Adobe Commerce-Patch MCP-87 hat das Problem behoben, dass die Neuindizierung von Katalogen nur langsam durchgeführt werden konnte. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 installiert ist.
exl-id: 048b2764-6bbf-4a02-9a0a-dbea4e48f92a
feature: Storefront
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# MCP-87 Adobe Commerce Patch: Storefront defekt

Der Adobe Commerce-Patch MCP-87 hat das Problem behoben, dass die Neuindizierung von Katalogen nur langsam durchgeführt werden konnte. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 installiert ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf Cloud-Infrastruktur 2.4.0.

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1 - 2.4.1.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Neuindizierung von Katalogen mit großen Profilen ist sehr langsam.

<u>Zu reproduzierende Schritte:</u>

1. Melden Sie sich beim Admin Panel an.
1. Navigieren Sie zu: **Produkte** > **Katalog**.
1. Wählen Sie alle Elemente im Raster Produkte aus.
1. Wählen Sie **Attribute aktualisieren** in der Dropdown-Liste Produktaktionen auswählen aus. Klicken Sie auf **Senden**.
1. Klicken Sie auf der Registerkarte &quot;Erweiterte Einstellungen&quot;auf **Erweiterter Bestand** . Ändern Sie **Lagerverfügbarkeit** in *Auf Lager*. Klicken Sie auf **Speichern**.
1. Führen Sie die vollständige Neuindizierung manuell durch, führen Sie den folgenden Befehl aus dem Stammverzeichnis aus: `bin/magento indexer:reindex`

<u>Erwartetes Ergebnis:</u>

Der Aktienindex wird schnell neu indiziert.

<u>Tatsächliches Ergebnis:</u>

Der Aktienindex ist sehr langsam und/oder wird nicht abgeschlossen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
