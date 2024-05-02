---
title: Langsame Leistung aufgrund vollständiger Neuindizierung
description: Dieser Artikel enthält eine Fehlerbehebung für eine mangelhafte Leistung aufgrund der vollständigen Neuindizierung (wobei Daten in den indexbezogenen Datenbanktabellen aktualisiert werden).
exl-id: 4f20a862-cf54-4196-8a88-101f0c80f8f1
feature: Best Practices
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Langsame Leistung aufgrund vollständiger Neuindizierung

Dieser Artikel enthält eine Fehlerbehebung für eine mangelhafte Leistung aufgrund der vollständigen Neuindizierung (wobei Daten in den indexbezogenen Datenbanktabellen aktualisiert werden).

## Betroffene Versionen und Produkte

* Adobe Commerce auf Cloud-Infrastruktur 2.x.x
* Adobe Commerce On-Premise 2.x.x

### Problem

Die ständige Leerung und Neuerstellung von Indizes sind einige der Gründe für die Leistungsbeeinträchtigung. Darüber hinaus sorgt die ständige vollständige Neuindizierung für Sperren von Tabellen, wodurch die Website viel langsamer als erwartet funktioniert.

### Ursache

Aktionen, die eine vollständige Neuindizierung ermöglichen, wurden von Admin ausgeführt, darunter:

* Produktattribut speichern
* Speichern der Website-/Store-/Store-Ansicht
* Store-Konfiguration

>[!NOTE]
>
>Diese Aktionen sollten außerhalb der Geschäftszeiten ausgeführt werden, um sicherzustellen, dass sich diese Aktionen nicht auf die Leistung während der Geschäftszeiten auswirken.

[Drittanbietererweiterungen](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento) kann auch zu einer vollständigen Neuindizierung führen. Die vollständige Neuindizierung kann auch manuell über die CLI ausgeführt werden. Um herauszufinden, ob Indizes neu indiziert werden und möglicherweise eine Leistungsbeeinträchtigung verursachen:

1. Führen Sie diese Abfrage aus, um die Indexer zu finden, die in den letzten 15 Minuten vollständig neu indiziert wurden:

   ```
   SELECT * FROM indexer_state WHERE updated > NOW() - INTERVAL 15 MINUTE;
   ```

   Ein Indexname in der Ausgabe bedeutet, dass der Indexer in den letzten 15 Minuten mindestens einmal neu indiziert wurde.

1. Wenn bei Ihnen häufige vollständige Neuindizierung festgestellt wurde, untersuchen Sie Folgendes:
   * Wer kann dies manuell über die CLI tun?
   * Welche Drittanbietermodule die Neuindizierung durchführen
   * Das Modul eines Drittanbieters markiert Indexer als *Ungültig*

### Lösung

Führen Sie die Neuindizierung nur bei Bedarf aus. Informationen zu den Schritten finden Sie unter [Konfigurieren von Indexern](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html#configure-indexers) in unserer Entwicklerdokumentation. Eine allgemeine Empfehlung und Best Practice besteht darin, dem Mechanismus für die partielle Neuindizierung die Möglichkeit zu geben, sich um die Neuindizierung von Daten zu kümmern, ohne dass von einem Händler manuelle Maßnahmen erforderlich sind. Alle Neuindizierungen sollten mit nativen Adobe Commerce-Funktionen (Mview) durchgeführt werden. Mview führt eine partielle Neuindizierung durch, was die effizienteste Methode zur Neuindizierung von Daten ist. Weitere Informationen zur Ansicht finden Sie unter [Indizierungsübersicht: Übersicht](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#m2devgde-mview) in unserer Entwicklerdokumentation.

## Verwandte Informationen

* [Indizierungsübersicht: Neuindizierung](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#how-to-reindex) in unserer Entwicklerdokumentation.
* [Invalidierter Cache führt zu einer Verschlechterung der Reaktionszeit](/help/troubleshooting/miscellaneous/invalidated-cache-causes-response-time-degradation.md) in unserer Wissensdatenbank.
