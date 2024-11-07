---
title: Benutzerdefinierte Server-seitige Skripte, die nicht im Pub-Medienverzeichnis ausgeführt werden
description: Dieser Artikel enthält eine Fehlerbehebung für den Fall, dass benutzerdefinierte serverseitige Skripte nicht ausgeführt werden, wenn sie in ""platziert werden.Ordner /pub/media/ Ihrer Adobe Commerce-Anwendung in der Cloud-Infrastruktur. Dies ist eine erwartete Sicherheitsbegrenzung, da ".Der Ordner /pub/media/` ist schreibbar. Um Skripte ausführbar zu machen, platzieren Sie sie in nicht beschreibbaren Ordnern wie "./app/code/ oder `./pub/`.
exl-id: fcad8a5d-47d6-4729-93a4-2410d7710d69
feature: Media
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Benutzerdefinierte Server-seitige Skripte, die nicht im Pub-Medienverzeichnis ausgeführt werden

Dieser Artikel enthält eine Fehlerbehebung für den Fall, dass benutzerdefinierte serverseitige Skripte nicht ausgeführt werden, wenn sie im Ordner &quot;`./pub/media/`&quot;Ihrer Adobe Commerce-Anwendung in der Cloud-Infrastruktur abgelegt werden. Dies ist eine erwartete Sicherheitsbeschränkung, da das Verzeichnis `./pub/media/` schreibbar ist. Um Skripte ausführbar zu machen, platzieren Sie sie in nicht beschreibbaren Verzeichnissen wie `./app/code/` oder `./pub/`.

## Betroffene Versionen

* Adobe Commerce zur Cloud-Infrastruktur: 2.1.x und höher, Starter und Pro plant Architektur, Wings und ältere Architekturen

## Problem: Skripte werden nicht ausgeführt

Benutzerdefinierte serverseitige Skripte können nicht ausgeführt werden, wenn sie initiiert werden.

Wenn beispielsweise der Endbenutzer (Adobe Commerce-Käufer) auf den Link klickt, der zur Datei &quot;`\*.php`&quot;mit dem Skript führt (z. B. &quot;*domain.com/media/directory/script.php*&quot;), wird das Skript heruntergeladen, anstatt es auszuführen.

## Ursache: falscher Speicherort der Skriptdatei

Das Problem tritt auf, wenn sich die Skriptdateien im Ordner &quot;`./pub/media/`&quot;der Adobe Commerce-Anwendung in der Cloud-Infrastruktur befinden. Dies ist ein erwartetes Verhalten: Aufgrund von Sicherheitsbeschränkungen werden Dateien aus den beschreibbaren Verzeichnissen (`./pub/media/`) nie ausgeführt.

## Lösung: Platzieren Sie Skripte in nicht beschreibbaren Verzeichnissen

Speichern Sie die Server-seitigen Skripte in nicht schreibgeschützten Verzeichnissen wie `./app/code/` oder `./pub/` &quot;

## Verwandte Dokumentation

* [Cloud für Adobe Commerce > Projektstruktur > Schreibfähige Verzeichnisse](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/file-structure#writable-directories) in unserer Entwicklerdokumentation.
