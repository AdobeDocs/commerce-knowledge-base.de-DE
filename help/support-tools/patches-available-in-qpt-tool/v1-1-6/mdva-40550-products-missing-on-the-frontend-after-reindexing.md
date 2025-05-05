---
title: 'MDVA-40550: Produkte fehlen nach der Neuindizierung im Frontend'
description: Der Patch MDVA-40550 löst das Problem, dass eine Neuindizierung dazu führt, dass einige oder alle Storefront-Kategorien Produkte vermissen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-40550. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
exl-id: 0aca6eb2-6eb2-4ac4-8ae1-052f671c14e5
feature: Categories, Console, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MDVA-40550: Produkte fehlen nach der Neuindizierung im Frontend

Der Patch MDVA-40550 löst das Problem, dass eine Neuindizierung dazu führt, dass einige oder alle Storefront-Kategorien Produkte vermissen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-40550. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Produkt.
1. Wechseln Sie zu **Nach Zeitplan aktualisieren**.
   * Weisen Sie das Produkt einer Kategorie zu.
1. Aktivieren Sie xdebug und machen Sie xdebug Breakpoint in `\Magento\Indexer\Model\Indexer::reindexAll` und `\Magento\Indexer\Model\IndexMutex::execute`.
1. Führen Sie eine **vollständige Neuindizierung** von `catalog_category_product` mit folgendem Befehl aus:

   ```bash
   bin/magento indexer:reindex catalog_category_product
   ```

   * Warten Sie, bis die Ausführung am Haltepunkt `\Magento\Indexer\Model\Indexer::reindexAll` beendet ist.

1. Führen Sie in einer anderen Konsole **teilweise Neuindizierung** parallel zum Befehl aus:

   ```bash
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Warten Sie, bis die Ausführung am Haltepunkt `\Magento\Indexer\Model\IndexMutex::execute` beendet ist. Dadurch wird der `catalog_category_product` Indexer gesperrt.
1. Setzt die Ausführung der vollständigen Neuindizierung von `catalog_category_product` fort und wartet auf eine Sperr-Zeitüberschreitung (60 Sekunden).

<u>Erwartete Ergebnisse</u>:

Keine Fehlermeldungen in der Konsole.

<u>Tatsächliche Ergebnisse</u>:

Es wird die folgende Fehlermeldung angezeigt:

*Sperre für Index konnte nicht abgerufen werden: catalog_category_product.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
