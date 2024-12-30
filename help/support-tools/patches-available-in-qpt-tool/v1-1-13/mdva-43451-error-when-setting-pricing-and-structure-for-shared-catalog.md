---
title: 'MDVA-43451: Fehler beim Festlegen von Preisen und Struktur für freigegebenen Katalog'
description: Der Patch MDVA-43451 löst das Problem, dass der Benutzer die Preise und die Struktur für einen freigegebenen Katalog nicht festlegen kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43451. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: 78de2e98-dfd7-4829-8e3f-76eadf5570e8
feature: Catalog Management
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# MDVA-43451: Fehler beim Festlegen von Preisen und Struktur für freigegebenen Katalog

Der Patch MDVA-43451 löst das Problem, dass der Benutzer die Preise und die Struktur für einen freigegebenen Katalog nicht festlegen kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43451. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzende können keine Preise und Strukturen für einen freigegebenen Katalog festlegen. Die folgende Meldung wird angezeigt: *Der angeforderte Store wurde nicht gefunden. Überprüfen Sie den Store und versuchen Sie es erneut.*

<u>Schritte zur Reproduktion</u>:

1. Erstellen einer benutzerdefinierten Website. Die IDs der Websites sollten 0, 1, 2 sein.
1. Erstellen Sie einen Store unter der obigen Website. Die IDs der Stores sollten 0,1,2 sein.
1. Erstellen Sie drei Store-Ansichten für den obigen Store. Die IDs der Store-Ansichten sollten 0,1, 2, 3, 4 sein.
1. Löschen Sie die Store-Ansicht mit der ID 2. Jetzt sollte die Store-Tabelle in etwa wie die folgende Tabelle aussehen.

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

Der freigegebene Katalog wird problemlos gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Der freigegebene Katalog kann nicht gespeichert werden. Der folgende Fehler wird angezeigt:
*Der angeforderte Store wurde nicht gefunden. Überprüfen Sie den Store und versuchen Sie es erneut.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in unserer Entwicklerdokumentation.
