---
title: "MDVA-43451: Fehler beim Festlegen von Preisen und Struktur für freigegebenen Katalog"
description: Der Patch MDVA-43451 behebt das Problem, dass der Benutzer die Preise und Struktur für einen freigegebenen Katalog nicht festlegen kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43451. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: 78de2e98-dfd7-4829-8e3f-76eadf5570e8
feature: Catalog Management
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# MDVA-43451: Fehler beim Festlegen von Preisen und Struktur für freigegebenen Katalog

Der Patch MDVA-43451 behebt das Problem, dass der Benutzer die Preise und Struktur für einen freigegebenen Katalog nicht festlegen kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43451. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Benutzer kann die Preise und Struktur für einen freigegebenen Katalog nicht festlegen. Die folgende Meldung wird angezeigt: *Der angeforderte Speicher wurde nicht gefunden. Überprüfen Sie den Store und versuchen Sie es erneut.*

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine benutzerdefinierte Website. Die IDs der Websites sollten 0, 1, 2 sein.
1. Erstellen Sie einen Store unter der obigen Website. Die IDs der Geschäfte sollten 0,1,2 sein.
1. Erstellen Sie drei Store-Ansichten für den obigen Store. Die IDs der Store-Ansichten sollten 0,1, 2, 3, 4 sein.
1. Löschen Sie die Store-Ansicht mit ID 2. Die Store-Tabelle sollte nun ähnlich wie die unten stehende Tabelle aussehen.

   ```bash
   MariaDB [m24devinvb2b]> SELECT store_id,code,website_id,group_id,name FROM store;
   +----------+----------------+------------+----------+--------------------+
   | store_id | code           | website_id | group_id | name               |
   +----------+----------------+------------+----------+--------------------+
   |        0 | admin          |          0 |        0 | Admin              |
   |        1 | default        |          1 |        1 | Default Store View |
   |        3 | web1storeview2 |          2 |        2 | web1storeview2     |
   |        4 | web1storeview3 |          2 |        2 | web1storeview3     |
   +----------+----------------+------------+----------+--------------------+
   ```

1. Erstellen Sie einen neuen freigegebenen Katalog.
1. Wählen Sie beim Konfigurieren von Preis und Struktur den in Schritt 2 erstellten Store aus.
1. Speichern Sie den freigegebenen Katalog.

<u>Erwartete Ergebnisse</u>:

Der freigegebene Katalog wird ohne Probleme gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Sie können den freigegebenen Katalog nicht speichern. Der folgende Fehler wird angezeigt:
*Der angeforderte Store wurde nicht gefunden. Überprüfen Sie den Store und versuchen Sie es erneut.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
