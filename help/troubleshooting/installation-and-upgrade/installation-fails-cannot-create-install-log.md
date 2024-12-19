---
title: Installation schlägt fehl; install.log kann nicht erstellt werden
description: Dieser Artikel enthält eine Fehlerbehebung für eine fehlgeschlagene Installation, da der Setup-Assistent während der Installation „install.log“ nicht erstellt hat.
exl-id: ff614018-8e49-4170-a806-8ebdc91ae8a9
feature: Install, Logs, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Installation schlägt fehl; install.log kann nicht erstellt werden

Dieser Artikel enthält eine Fehlerbehebung für eine fehlgeschlagene Installation, die darauf zurückzuführen ist, dass der Setup-Assistent während der Installation die `install.log` nicht erstellt hat.

## Problem

Das gleichzeitige Ausführen von Adobe Commerce-Prozessen kann zu Problemen beim Erstellen des Installationsprotokolls führen. (Beispiel: zwei verschiedene Installationen auf separaten Registerkarten.)

## Ursache

Installation-failed-cannot-create-install.log
Überprüfen Sie Ihre Einstellung für `open_basedir` in `php.ini`. Der Setup-Assistent verwendet den PHP-Aufruf [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php), um den Wert des temporären Verzeichnisses abzurufen. Wenn [open\_basedir](http://php.net/manual/en/ini.core.php#ini.open-basedir) so eingestellt ist, dass Verbindungen zu einem von `sys_get_temp_dir` angegebenen Verzeichnis verweigert werden, schlägt die Installation fehl.
Überprüfen Sie Ihre Einstellung für `open_basedir` in `php.ini`. Der Setup-Assistent verwendet den PHP-Aufruf [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php), um den Wert des temporären Verzeichnisses abzurufen. Wenn [open\_basedir](https://php.net/manual/en/ini.core.php#ini.open-basedir) so eingestellt ist, dass Verbindungen zu einem von `sys_get_temp_dir` angegebenen Verzeichnis verweigert werden, schlägt die Installation fehl.


## Lösung

Um das Problem zu beheben, ändern Sie den Wert von `open_basedir` und starten Sie den Webserver neu.

Wenn Sie sich nicht sicher sind, wie Sie diesen Wert ändern, führen Sie die folgenden Schritte aus:

1. Falls noch nicht geschehen, erstellen Sie [phpinfo.php](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software).
1. Geben Sie die folgende URL in das Feld Adresse oder Standort Ihres Browsers ein: `https://<your web server IP or hostname>/<path to docroot>/phpinfo.php`
1. Suchen Sie nach dem Speicherort von `php.ini`.     `php.ini` wird in der Regel als **Geladene Konfigurationsdatei** in den angezeigten Ergebnissen angegeben.
1. Wenn Sie als Benutzer mit Root-Berechtigungen sind, öffnen Sie `php.ini` in einem Texteditor.
1. Suchen Sie den Wert von `open_basedir` und ändern Sie ihn.
1. Speichern Sie Ihre Änderungen in `php.ini`.
1. Starten Sie den Webserver neu.
