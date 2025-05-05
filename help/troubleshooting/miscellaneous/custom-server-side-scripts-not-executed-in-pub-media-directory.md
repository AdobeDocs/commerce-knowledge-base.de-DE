---
title: Benutzerdefinierte Server-seitige Skripte werden im Veröffentlichungsmedienverzeichnis nicht ausgeführt
description: Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass benutzerdefinierte Server-seitige Skripte nicht ausgeführt werden, wenn sie in der "" platziert werden./pub/media/&grave;-Verzeichnis Ihrer Adobe Commerce-Anwendung in der Cloud-Infrastruktur. Dies ist eine erwartete Sicherheitsbeschränkung, da der "".Der Ordner "/pub/media/&grave;" ist schreibbar. Damit Skripte ausführbar werden, müssen sie in nicht beschreibbaren Verzeichnissen, wie z. B. "", abgelegt werden./app/code/&grave; oder "./pub/&grave;.
exl-id: fcad8a5d-47d6-4729-93a4-2410d7710d69
feature: Media
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Benutzerdefinierte Server-seitige Skripte werden im Veröffentlichungsmedienverzeichnis nicht ausgeführt

Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass benutzerdefinierte Server-seitige Skripte nicht ausgeführt werden, wenn sie im `./pub/media/` Verzeichnis Ihrer Adobe Commerce-Anwendung in der Cloud-Infrastruktur platziert werden. Dies ist eine erwartete Sicherheitsbeschränkung, da das `./pub/media/` beschreibbar ist. Um Skripte ausführbar zu machen, platzieren Sie sie in nicht beschreibbaren Verzeichnissen, wie `./app/code/` oder `./pub/`.

## Betroffene Versionen

* Adobe Commerce auf Cloud-Infrastruktur: 2.1.x und höher, Starter und Pro plant Architektur, Wings und Legacy-Architekturen

## Problem: Skripte nicht ausgeführt

Benutzerdefinierte Server-seitige Skripte können bei Initiierung nicht ausgeführt werden.

Wenn der Endbenutzer (Adobe Commerce-Käufer) beispielsweise auf den Link klickt, der zu der `\*.php` mit dem Skript führt (z. B. *domain.com/media/directory/script.php* ), wird das Skript heruntergeladen statt ausgeführt.

## Ursache: Falscher Speicherort der Skriptdatei

Das Problem tritt auf, wenn sich die Skriptdateien im `./pub/media/` des Adobe Commerce-Programms in der Cloud-Infrastruktur befinden. Dies ist ein erwartetes Verhalten: Aufgrund von Sicherheitsbeschränkungen werden Dateien aus den beschreibbaren Verzeichnissen (`./pub/media/`) nie ausgeführt.

## Lösung: Platzieren von Skripten in nicht beschreibbaren Verzeichnissen

Speichern Sie die Server-seitigen Skripte in nicht beschreibbaren Verzeichnissen, z. B. `./app/code/` oder `./pub/` &quot;

## Verwandte Dokumentation

* [Cloud für Adobe Commerce > Projektstruktur > Schreibbare Verzeichnisse](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/project/file-structure#writable-directories) in unserer Entwicklerdokumentation.
