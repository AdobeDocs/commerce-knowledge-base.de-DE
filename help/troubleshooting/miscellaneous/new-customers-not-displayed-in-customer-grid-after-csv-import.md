---
title: Neue Kunden werden nach dem CSV-Import nicht im Kundenraster angezeigt
description: Dieser Artikel enthält eine Fehlerbehebung für das Problem, wenn Sie unter "Kunden** und gt; **Alle Kunden** nach einem Import aus einer CSV-Datei keine neuen Kunden sehen können. Die Lösung besteht darin, den Indexer "customer_grid"auf den Modus "Update on Save"festzulegen und das Kundenraster manuell neu zu indizieren.
exl-id: e4d9d60a-a0d1-4602-924e-a338e56de61d
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Neue Kunden werden nach dem CSV-Import nicht im Kundenraster angezeigt

Dieser Artikel enthält eine Fehlerbehebung für das Problem, wenn neue Kunden unter nicht angezeigt werden können. **Kunden** > **Alle Kunden** nach einem Import aus einem `.csv` -Datei. Die Lösung besteht darin, die `customer_grid` Indexer in den Modus &quot;Auf Speichern aktualisieren&quot;und indizieren das Kundenraster manuell neu.

## Betroffene Versionen

* Adobe Commerce On-Premise 2.2.0 und höher
* Adobe Commerce auf Cloud-Infrastruktur 2.2.0 und höher

## Problem

Nach dem Import neuer Kunden aus einer `.csv` mit der nativen Adobe Commerce-Importfunktion verwenden, können Sie die neuen Kundendatensätze möglicherweise nicht unter **Kunden** > **Alle Kunden** in Admin, bis Sie die `customer_grid` Indexer.

## Ursache

Der Indexierungsmodus &quot;Auf Zeitplan aktualisieren&quot;in Adobe Commerce 2.2.0 und höher unterstützt nicht die `customer_grid` Indexer aufgrund von Leistungsproblemen.

## Lösung

Konfigurieren Sie die `customer_grid` Indexer, der im Modus &quot;Beim Speichern aktualisieren&quot;neu indiziert werden soll. Gehen Sie dazu wie folgt vor:

1. Melden Sie sich bei Commerce Admin an.
1. Klicks **System** > **Instrumente** > **Indexverwaltung**.
1. Aktivieren Sie das Kontrollkästchen neben Customer Grid Indexer.
1. Im **Aktionen** Dropdown-Liste auswählen *Beim Speichern aktualisieren*.
1. Klicks **Einsenden**.

Es wird außerdem empfohlen, die `customer_grid` Indexer nach der Konfiguration des Indizierungsmodus, um sicherzustellen, dass der Index aktuell ist und mit Cron arbeiten kann. Verwenden Sie den folgenden Befehl, um eine manuelle Neuindizierung durchzuführen:

`bin/magento indexer:reindex customer_grid`

## Weitere Informationen

Links zu verwandten Themen in unserer Entwicklerdokumentation:

* [Indizierungsübersicht](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html)
* [Indexer verwalten](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html)
