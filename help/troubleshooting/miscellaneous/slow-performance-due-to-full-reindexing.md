---
title: Langsame Leistung aufgrund vollständiger Neuindizierung
description: Dieser Artikel bietet eine Korrektur für die schlechte Leistung aufgrund einer vollständigen Neuindizierung (bei der Daten in den indizierungsbezogenen Datenbanktabellen aktualisiert werden).
exl-id: 4f20a862-cf54-4196-8a88-101f0c80f8f1
feature: Best Practices
role: Developer
source-git-commit: 72ee49a8667f575a58e0cf1b3d5c9df936cc628b
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Langsame Leistung aufgrund vollständiger Neuindizierung

Dieser Artikel bietet eine Korrektur für die schlechte Leistung aufgrund einer vollständigen Neuindizierung (bei der Daten in den indizierungsbezogenen Datenbanktabellen aktualisiert werden).

## Betroffene Versionen und Produkte

* Adobe Commerce auf Cloud-Infrastruktur 2.x.x
* Adobe Commerce On-Premises 2.x.x

### Problem

Ständiges Spülen und Neuerstellen des Index sind einige der Gründe für Leistungseinbußen. Darüber hinaus werden Tabellen durch eine konstante vollständige Neuindizierung gesperrt, was dazu führt, dass die Website viel langsamer als erwartet funktioniert.

### Ursache

Vom Administrator wurden Aktionen ausgeführt, die eine vollständige Neuindizierung ermöglichen, darunter:

* Produktattribut speichern
* Website-/Store-/Store-Ansicht speichern
* Store-Konfiguration

>[!NOTE]
>
>Diese Aktionen sollten außerhalb der Geschäftszeiten ausgeführt werden, um sicherzustellen, dass diese Aktionen die Leistung während der Geschäftszeiten nicht beeinträchtigen.

[Erweiterungen von Drittanbietern](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento) können auch zu einer vollständigen Neuindizierung führen. Die vollständige Neuindizierung kann auch manuell über die CLI ausgeführt werden. So ermitteln Sie, ob Indizes neu indiziert werden und möglicherweise zu Leistungseinbußen führen:

1. Führen Sie diese Abfrage aus, um die Indexer zu finden, die in den letzten 15 Minuten vollständig neu indiziert wurden:

   ```
   SELECT * FROM indexer_state WHERE updated > NOW() - INTERVAL 15 MINUTE;
   ```

   Ein Indexername in der Ausgabe bedeutet, dass der Indexer in den letzten 15 Minuten mindestens einmal neu indiziert wurde.

1. Wenn Sie häufige vollständige Neuindizierungen gefunden haben, untersuchen Sie Folgendes:
   * Personen, die dies möglicherweise manuell über die CLI durchführen
   * Welches Drittanbietermodul führt die Neuindizierung durch?
   * Welches Drittanbietermodul kennzeichnet Indexer als *ungültig*

### Lösung

Führen Sie die Neuindizierung nur aus, wenn erforderlich. Anweisungen hierzu finden Sie [Konfigurieren von ](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers)) in unserer Entwicklerdokumentation. Eine allgemeine Empfehlung und Best Practice ist es, dem Mechanismus der partiellen Neuindizierung zu ermöglichen, die Neuindizierung von Daten zu übernehmen, ohne dass ein Händler manuelle Maßnahmen ergreifen muss. Alle Neuindizierungen sollten mit der nativen Adobe Commerce-Funktion (Mview) durchgeführt werden. Mview führt eine partielle Neuindizierung durch, was die effizienteste Methode zur Neuindizierung von Daten ist. Weitere Informationen zu Mview finden Sie unter [Indizierungsübersicht: Mview](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

* [Indizierungsübersicht: So indizieren Sie ](https://developer.adobe.com/commerce/php/development/components/indexing/#how-to-reindex) in unserer Entwicklerdokumentation.
* [Ungültiger Cache verursacht eine Verschlechterung der Reaktionszeit](/help/troubleshooting/miscellaneous/invalidated-cache-causes-response-time-degradation.md) in unserer Support-Wissensdatenbank.

