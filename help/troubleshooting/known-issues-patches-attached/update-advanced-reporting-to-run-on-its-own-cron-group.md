---
title: Aktualisierung der erweiterten Berichterstellung für die Ausführung auf eigene Cron-Gruppe
description: Dieser Artikel enthält einen Patch für das bekannte Problem für Adobe Commerce in der Cloud-Infrastruktur 2.3.0, bei dem die erweiterte Berichterstellung keine Daten anzeigt. Dies liegt daran, dass der erweiterte Berichtsauftrag "analytics_collect_data"nicht planmäßig ausgeführt wird. Dieser Artikel enthält einen Patch, der eine Cron-Gruppe "Analyse"für erweiterte Berichte erstellt.
exl-id: 8aff9e2b-d9be-4136-975b-05963e23f55c
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Aktualisierung der erweiterten Berichterstellung für die Ausführung auf eigene Cron-Gruppe

Dieser Artikel enthält einen Patch für das bekannte Problem für Adobe Commerce in der Cloud-Infrastruktur 2.3.0, bei dem die erweiterte Berichterstellung keine Daten anzeigt. Dies liegt daran, dass der erweiterte Berichtsauftrag `analytics_collect_data` nicht planmäßig ausgeführt wird. Dieser Artikel enthält einen Patch, der eine Cron-Gruppe für erweiterte Berichte erstellt `analytics`.

## Problem

In das Modul &quot;Erweiterte Berichterstellung&quot;werden keine Daten geladen.

## Patch

Der Patch ist an diesen Artikel angehängt. Der Patch verschiebt den `analytics` Cron-Auftragsaufgaben von der Standardgruppe in `analytics`.

Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-19640\_EE\_2.3.0\_COMPOSER\_v1.patch](assets/MDVA-19640_EE_2.3.0_COMPOSER_v1.patch.zip)

Führen Sie nach dem Anwenden des Patches die folgende SQL-Abfrage aus. Die Abfrage muss ausgeführt werden, um Datensätze in `cron_schedule` Tabelle.

```
UPDATE core_config_data
SET `path` = REPLACE(path, "crontab/default/jobs/analytics", "crontab/analytics/jobs/analytics")
WHERE `path` LIKE "crontab/default/jobs/analytics%";
```

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt.

* Adobe Commerce auf Cloud-Infrastruktur 2.3.0

Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem aber möglicherweise nicht): 2.2.2-2.2.10, 2.3.0-2.3.2 und 2.3.2-p2 und 2.3.3.3 für Adobe Commerce On-Premise und Adobe Commerce für Cloud-Infrastruktur

## Anwenden des Pflasters

Siehe [Anwenden eines von Adobe bereitgestellten Composer-Patches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) für Anweisungen.

## Attached files
