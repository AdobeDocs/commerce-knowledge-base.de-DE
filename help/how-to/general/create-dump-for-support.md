---
title: Erstellen eines „Bereinigungs“-Dump auf Anfrage des Support-Mitarbeiters
description: Dieser Artikel enthält Informationen dazu, wie Sie einen „Bereinigten“ Dump (Backup) Ihrer Datenbank und Ihres Codes vom Adobe Commerce-Administrator erstellen, wenn Sie von einem Adobe Commerce-Support-Agenten dazu aufgefordert werden. Dieser Dump schließt Ihre Mediendateien aus, um den Prozess zu beschleunigen und eine viel kleinere Datei zu erhalten. Bei der Datenbanksicherung werden alle sensiblen Daten gehasht.
exl-id: ad088bd2-3f92-416e-89f0-d037d53cd6a9
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%
---
# Erstellen eines „Bereinigungs“-Dump auf Anfrage des Support-Mitarbeiters


## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.x, 2.4.x.

## Erstellen eines „bereinigten“ Speicherauszugs

Erstellen Sie einen „bereinigten“ Dump vom Administrator:

1. Wechseln Sie in Commerce Admin zu **System** > **Support** > **Datenerfassung**.
1. Klicken Sie **Neue Sicherung**.
1. Klicken Sie nach einigen Minuten auf **Status aktualisieren** (kann länger dauern und alle 5 Minuten bis zum Abschluss wiederholt werden).
1. Verschieben Sie die generierten Dump-Dateien aus dem `/var/support` in das Adobe Commerce-Stammverzeichnis.

Sie können dann für den Support den direkten Download-Link zu den Dump-Dateien angeben (Ihre Store-Adresse und der Dateiname wie angezeigt).

Wenn Sie beim Erstellen von Dumps über die Admin Probleme haben, sollten Sie CLI-Befehle verwenden, wie unter [Ausführen der Support-Dienstprogramme](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cli/run-support-utilities) in unserer Entwicklerdokumentation beschrieben.

## Verwandtes Lesen

* [Erstellen Sie vollständige Datenbanksicherung für Adobe Commerce in der Cloud](/help/how-to/general/create-database-dump-on-cloud.md)Infrastruktur in unserer Support-Wissensdatenbank.
