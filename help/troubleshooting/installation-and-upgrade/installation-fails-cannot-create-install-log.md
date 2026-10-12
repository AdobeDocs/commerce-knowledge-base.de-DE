---
title: Installation schlägt fehl; install.log kann nicht erstellt werden
description: Dieser Artikel enthält eine Fehlerbehebung für eine fehlgeschlagene Installation, da der Setup-Assistent während der Installation „install.log“ nicht erstellt hat.
exl-id: ff614018-8e49-4170-a806-8ebdc91ae8a9
feature: Install, Logs, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: 3c398179-d35a-51ba-b317-6c5b95feef5e
    internal-label: Logs
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '283'
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

1. Falls noch nicht geschehen, erstellen Sie [phpinfo.php](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/prerequisites/optional-software).
1. Geben Sie die folgende URL in das Feld Adresse oder Standort Ihres Browsers ein: `https://<your web server IP or hostname>/<path to docroot>/phpinfo.php`
1. Suchen Sie nach dem Speicherort von `php.ini`. `php.ini` wird normalerweise als **geladene Konfigurationsdatei** in den angezeigten Ergebnissen angegeben.
1. Wenn Sie als Benutzer mit Root-Berechtigungen sind, öffnen Sie `php.ini` in einem Texteditor.
1. Suchen Sie den Wert von `open_basedir` und ändern Sie ihn.
1. Speichern Sie Ihre Änderungen in `php.ini`.
1. Starten Sie den Webserver neu.
