---
title: Erstellen einer "gescrubten"-Ablage auf Anforderung durch den Support-Mitarbeiter
description: In diesem Artikel erfahren Sie, wie Sie eine gescannte Sicherungskopie (Backup) Ihrer Datenbank erstellen und vom Adobe Commerce-Administrator Code bereitstellen können, wenn Sie von einem Adobe Commerce-Support-Mitarbeiter dazu aufgefordert werden. In diesem Dump werden Ihre Mediendateien ausgeschlossen, um den Prozess zu beschleunigen und eine wesentlich kleinere Datei zu erzeugen. Alle sensiblen Daten werden beim Erstellen der Datenbanksicherung gehasht.
exl-id: ad088bd2-3f92-416e-89f0-d037d53cd6a9
source-git-commit: e07ade849a4105b5e499b5282d75cb1b5321b6ea
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# Erstellen einer &quot;gescrubten&quot;-Ablage auf Anforderung durch den Support-Mitarbeiter


## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.x, 2.4.x.

## Erstellen einer &quot;gescrubten&quot;-Dump

Erstellen Sie eine &quot;gescrubbt&quot;-Dump vom Administrator:

1. Wechseln Sie in Commerce Admin zu **System** > **Support** > **Datenerfassung**.
1. Klicken Sie auf **Neues Backup**.
1. Klicken Sie nach einigen Minuten auf **Status aktualisieren** (kann länger dauern und alle 5 Minuten wiederholen, bis der Vorgang abgeschlossen ist).
1. Platzieren Sie die generierten Dump-Dateien aus dem Ordner &quot;`/var/support`&quot;in den Stammordner von Adobe Commerce.

Sie können dann angeben, um den direkten Download-Link zu den Dump-Dateien zu unterstützen (Ihre Store-Adresse und der Dateiname wie angezeigt).

Wenn Sie Probleme beim Erstellen von Dumps aus dem Admin haben, sollten Sie die Verwendung von CLI-Befehlen in Erwägung ziehen, wie unter [Ausführen der Support-Dienstprogramme](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-spt-util.html) in unserer Entwicklerdokumentation beschrieben.

## Verwandtes Lesen

* [Erstellen Sie eine vollständige Datenbanksicherung für Adobe Commerce in der Cloud-Infrastruktur](/help/how-to/general/create-database-dump-on-cloud.md) in unserer Support-Wissensdatenbank.
