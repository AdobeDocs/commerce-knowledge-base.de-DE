---
title: Das Berechtigungsproblem mit der Var/dem Exportordner Adobe Commerce in der Cloud
description: Dieser Artikel bietet eine Lösung für ein Problem, bei dem Sie aufgrund eines Problems mit den Dateiberechtigungen auf dem Server im Ordner „var/export/email“ keine Produktdaten exportieren können. Zu den Symptomen gehören Produkt- und Katalogexporte, die nicht in der Benutzeroberfläche verfügbar sind, aber bei Verwendung von SSH sichtbar sind.
exl-id: 68120d3b-f5df-43a5-91f6-2ec519cc25ac
feature: Cloud, Communications, Data Import/Export, Paas, Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Das Berechtigungsproblem mit der Var/dem Exportordner Adobe Commerce in der Cloud

Dieser Artikel bietet eine Lösung für ein Problem, bei dem Sie aufgrund eines Problems mit den Dateiberechtigungen auf dem Server im `var/export/email` keine Produktdaten exportieren können. Zu den Symptomen gehören Produkt- und Katalogexporte, die nicht in der Benutzeroberfläche verfügbar sind, aber bei Verwendung von SSH sichtbar sind.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur, 2.3.0-2.3.7-p2, 2.4.0-2.4.3-p1

## Problem

Dateien im `var/export/email` oder `var/export/archive` Ordner können nicht exportiert werden.
Die Bereitstellung ist aufgrund von Berechtigungen für `var/export/email` oder `var/export/email/archive` fehlgeschlagen, da dieser Archivordner unter E-Mail erstellt wird und bei einem Export/einer E-Mail manchmal noch ein Problem auftritt), außer dass etwas zum Konto für den Unterordner `var/export/email/archive` hinzugefügt wird.

<u>Schritte zur Reproduktion</u>:

Gehen Sie in der Admin zu **System** > *Datenübertragung* > **Exportieren**.
Wählen Sie die CSV-Dateien aus, die im `var/export/` gespeichert werden sollen.

<u>Erwartetes Ergebnis</u>:

CSV-Dateien sind sichtbar und können exportiert werden.

<u>Tatsächliches </u>:

CSV-Dateien sind nicht sichtbar. Außerdem wird die Meldung „Berechtigung verweigert“ angezeigt: *RecursiveDirectoryIterator::__konstrukt(/app/project id>/var/export/email): Verzeichnis konnte nicht geöffnet werden: Berechtigung verweigert*

Sie erhalten dieselbe Nachricht für alle Exporttypen: Erweiterte Preise, Kundenfinanzen, Hauptdatei des Kunden und Kundenadressen.

## Ursache

Dies wird durch einen Ordner verursacht, der in `/var` erstellt wurde und unvollständige Berechtigungen aufweist: `d-wxrwsr-T`. Das T-Sticky-Bit bedeutet, dass die Benutzer nur die Dateien löschen können, die sie besitzen, aber die fehlende ausführbare Datei bedeutet, dass sie keine Dateien im Verzeichnis erstellen können.

Dies wird häufig bemerkt, wenn das System einen Ordner mit dem Namen `export` erstellt, der einen Ordner mit dem Namen `email` enthält, der einen Ordner mit dem Namen `archive` enthält.

Um zu überprüfen, ob das Verzeichnis über diese falsch konfigurierten Berechtigungen verfügt, führen Sie den folgenden Befehl in der CLI/Terminal aus:

`ls -ld var/export/`

Die Ausgabe bei falsch konfigurierten Berechtigungen lautet:

`d-wxrwsr-T 3 web web 4096 Aug 15 19:12 var/export/`


## Lösung

Aktualisieren Sie dazu die Berechtigungen der Ordner auf 777 und dann alle Dateien rekursiv, indem Sie die folgenden Befehle ausführen:

```bash
chmod 777 var/export/
chmod 777 var/export/email/
chmod 777 var/export/email/archive/
chmod 777 -R var/export/
```

## Verwandtes Lesen

* [Export](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-export) in unserem Benutzerhandbuch.
