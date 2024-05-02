---
title: Benutzerdefinierte Server-seitige Skripte, die nicht im Pub-Medienverzeichnis ausgeführt werden
description: Dieser Artikel enthält eine Fehlerbehebung für den Fall, dass benutzerdefinierte serverseitige Skripte nicht ausgeführt werden, wenn sie in ""platziert werden.Ordner /pub/media/ Ihrer Adobe Commerce-Anwendung in der Cloud-Infrastruktur. Dies ist eine erwartete Sicherheitsbegrenzung, da ".Der Ordner /pub/media/` ist schreibbar. Um Skripte ausführbar zu machen, platzieren Sie sie in nicht beschreibbaren Ordnern wie "./app/code/ oder `./pub/`.
exl-id: fcad8a5d-47d6-4729-93a4-2410d7710d69
feature: Media
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Benutzerdefinierte Server-seitige Skripte, die nicht im Pub-Medienverzeichnis ausgeführt werden

Dieser Artikel enthält eine Fehlerbehebung für den Fall, dass benutzerdefinierte serverseitige Skripte nicht ausgeführt werden, wenn sie im `./pub/media/` Verzeichnis Ihrer Adobe Commerce-Anwendung in der Cloud-Infrastruktur. Dies ist eine erwartete Sicherheitsbeschränkung, da die Variable `./pub/media/` -Verzeichnis schreibbar ist. Um Skripte ausführbar zu machen, platzieren Sie sie in nicht beschreibbaren Ordnern, z. B. `./app/code/` oder `./pub/`.

## Betroffene Versionen

* Adobe Commerce zur Cloud-Infrastruktur: 2.1.x und höher, Starter und Pro plant Architektur, Wings und ältere Architekturen

## Problem: Skripte werden nicht ausgeführt

Benutzerdefinierte serverseitige Skripte können nicht ausgeführt werden, wenn sie initiiert werden.

Wenn beispielsweise der Endbenutzer (Adobe Commerce-Käufer) auf den Link klickt, der zu der `\*.php` Datei mit dem Skript (wie *domain.com/media/directory/script.php* ), wird das Skript heruntergeladen, anstatt es auszuführen.

## Ursache: falscher Speicherort der Skriptdatei

Das Problem tritt auf, wenn sich die Skriptdateien im `./pub/media/` Verzeichnis der Adobe Commerce-Anwendung in der Cloud-Infrastruktur. Dies ist ein erwartetes Verhalten: Aufgrund von Sicherheitsbeschränkungen werden Dateien aus den beschreibbaren Verzeichnissen (`./pub/media/`) nie ausgeführt werden.

## Lösung: Platzieren Sie Skripte in nicht beschreibbaren Verzeichnissen

Speichern Sie die serverseitigen Skripte in nicht schreibgeschützten Ordnern, z. B. `./app/code/` oder `./pub/`  &quot;

## Verwandte Dokumentation

* [Cloud für Adobe Commerce > Projektstruktur > Schreibbare Ordner](https://devdocs.magento.com/guides/v2.3/cloud/project/project-start.html#write-dir) in unserer Entwicklerdokumentation.
