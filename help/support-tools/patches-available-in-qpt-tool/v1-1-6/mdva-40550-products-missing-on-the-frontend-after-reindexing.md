---
title: "MDVA-40550: Produkte, die nach der Neuindizierung auf der Vorderseite fehlen"
description: Der Patch MDVA-40550 löst das Problem, dass die Neuindizierung dazu führt, dass einige oder alle Storefront-Kategorien Produkte fehlen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-40550. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: 0aca6eb2-6eb2-4ac4-8ae1-052f671c14e5
feature: Categories, Console, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MDVA-40550: Produkte, die nach der Neuindizierung auf der Vorderseite fehlen

Der Patch MDVA-40550 löst das Problem, dass die Neuindizierung dazu führt, dass einige oder alle Storefront-Kategorien Produkte fehlen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-40550. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Produkt.
1. Wechseln Sie in den Indexer zu **Nach Zeitplan aktualisieren** .
   * Weisen Sie das Produkt einer Kategorie zu.
1. Aktivieren Sie xdebug und machen Sie xdebug zum Haltepunkt in `\Magento\Indexer\Model\Indexer::reindexAll` und `\Magento\Indexer\Model\IndexMutex::execute`.
1. Führen Sie eine **vollständige Neuindizierung** von `catalog_category_product` mit dem Befehl aus:

   ```bash
   bin/magento indexer:reindex catalog_category_product
   ```

   * Warten Sie, bis die Ausführung am Haltepunkt `\Magento\Indexer\Model\Indexer::reindexAll` beendet wird.

1. Führen Sie in einer anderen Konsole parallel mit dem Befehl einen **partiellen Neuindizierungswert** aus:

   ```bash
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Warten Sie, bis die Ausführung am Haltepunkt `\Magento\Indexer\Model\IndexMutex::execute` beendet wird. Dadurch wird der `catalog_category_product`-Indexer gesperrt.
1. Setzt die Ausführung der vollständigen Neuindizierung von `catalog_category_product` fort und wartet auf eine Sperrzeitüberschreitung (60 Sekunden).

<u>Erwartete Ergebnisse</u>:

Keine Fehlermeldungen in der Konsole.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten den folgenden Fehler:

*Die Sperre für den Index konnte nicht erfasst werden: catalog_category_product.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
