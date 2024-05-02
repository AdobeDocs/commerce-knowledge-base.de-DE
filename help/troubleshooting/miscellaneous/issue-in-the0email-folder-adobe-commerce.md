---
title: Problem mit der Berechtigung für var-/export-Ordner in Adobe Commerce in Cloud
description: Dieser Artikel bietet eine Lösung für ein Problem, bei dem Sie aufgrund eines Problems mit Dateiberechtigungen auf dem Server im Ordner "var/export/email"keine Produktdaten exportieren können. Zu den Symptomen gehören Produkt- und Katalogexporte, die nicht in der Benutzeroberfläche verfügbar sind, aber bei Verwendung von SSH sichtbar sind.
exl-id: 68120d3b-f5df-43a5-91f6-2ec519cc25ac
feature: Cloud, Communications, Data Import/Export, Paas, Roles/Permissions
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Problem mit der Berechtigung für var-/export-Ordner in Adobe Commerce in Cloud

Dieser Artikel bietet eine Lösung für ein Problem, bei dem Sie aufgrund eines Problems mit Dateiberechtigungen auf dem Server im `var/export/email` Ordner. Zu den Symptomen gehören Produkt- und Katalogexporte, die nicht in der Benutzeroberfläche verfügbar sind, aber bei Verwendung von SSH sichtbar sind.

## Betroffene Produkte und Versionen

Adobe Commerce für Cloud-Infrastruktur, 2.3.0-2.3.7-p2, 2.4.0-2.4.3-p1

## Problem

Dateien können nicht im `var/export/email` oder `var/export/archive` Ordner.
Diese Bereitstellung ist aufgrund von Berechtigungen für fehlgeschlagen. `var/export/email` oder `var/export/email/archive` weil dieser Archivordner unter der E-Mail erstellt wird und wenn ich nur den Export/die E-Mail vornehme, gibt es manchmal noch ein Problem), das andere ist als das Hinzufügen von Elementen zum Unterordner `var/export/email/archive`.

<u>Zu reproduzierende Schritte</u>:

Navigieren Sie im Admin zu **System** > *Datenübertragung* > **Export**.
Wählen Sie die CSV-Dateien aus, die im `var/export/` Ordner.

<u>Erwartetes Ergebnis</u>:

CSV-Dateien sind sichtbar und können exportiert werden.

<u>Tatsächliches Ergebnis</u>:

CSV-Dateien sind nicht sichtbar. Außerdem wird die Meldung über die verweigerte Berechtigung angezeigt: *RecursiveDirectoryIterator::__struct(/app/project id>/var/export/email): Fehler beim Öffnen von Verzeichnis: Berechtigung verweigert*

Sie erhalten dieselbe Nachricht für alle Exporttypen: Erweiterte Preise, Kundenfinanzierungen, Hauptdatei des Kunden und Kundenadressen.

## Ursache

Dies wird durch einen Ordner verursacht, der in `/var` mit unvollständigen Berechtigungen: `d-wxrwsr-T`. Der &quot;Sticky&quot;-Bit bedeutet, dass die Benutzer nur die Dateien löschen können, deren Eigentümer sie sind. Die fehlende ausführbare Datei bedeutet jedoch, dass sie keine Dateien im Verzeichnis erstellen können.

Dies wird häufig bemerkt, wenn das System einen Ordner mit dem Namen `export`, der den Ordner enthält, der `email`, der den Ordner enthält, der `archive`.

Um zu überprüfen, ob das Verzeichnis über diese falsch konfigurierten Berechtigungen verfügt, führen Sie den folgenden Befehl in der CLI/Terminal aus:

`ls -ld var/export/`

Die Ausgabe, wenn Berechtigungen falsch konfiguriert sind, lautet:

`d-wxrwsr-T 3 web web 4096 Aug 15 19:12 var/export/`


## Lösung

Um dies zu beheben, aktualisieren Sie die Berechtigungen der Ordner auf 777 und dann rekursiv alle Dateien, indem Sie die folgenden Befehle ausführen:

```bash
chmod 777 var/export/
chmod 777 var/export/email/
chmod 777 var/export/email/archive/
chmod 777 -R var/export/
```

## Verwandtes Lesen

* [Export](https://docs.magento.com/user-guide/system/data-export.html) in unserem Benutzerhandbuch.
