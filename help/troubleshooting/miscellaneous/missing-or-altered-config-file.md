---
title: Fehlende oder geänderte Konfigurationsdatei
description: Beheben Sie das Problem mit fehlenden oder geänderten Konfigurationsdateien für Adobe Commerce.
exl-id: d80bf981-8ba6-4357-a841-57bf5d3f2a3f
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# Fehlende oder geänderte Konfigurationsdatei

In diesem Artikel wird beschrieben, wie Sie das Problem lösen können, dass Ihre Konfigurationsdateien geändert wurden oder fehlen.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle Versionen

## Problem

Konfigurationsdateien `config.php` und/oder `env.php` wurden falsch geändert oder fehlen.

## Lösung

Beim Bereitstellungsprozess wird für jede Konfigurationsdatei eine Sicherungsdatei erstellt:

* `app/etc/config.php.bak` - Enthält systemspezifische Einstellungen und wird beim Build automatisch generiert, wenn es noch nicht vorhanden ist
* `app/etc/env.php.bak` - enthält vertrauliche Konfigurationsdaten

Sie können sie mithilfe des Befehls ECE-Tools `backup:restore` wiederherstellen.

Die BAK-Dateien sind ein Produkt des Bereitstellungsprozesses. Wenn Sie eine Konfigurationsdatei nach der Bereitstellung manuell ändern, werden Ihre Änderungen nicht in den vorhandenen BAK-Dateien übernommen.

So stellen Sie die Konfigurationsdateien wieder her:

1. Melden Sie sich mit „SSH[ bei Ihrem Remote-Repository ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh).
1. Listet die verfügbaren Backup-Dateien auf.

   ```
   ./vendor/bin/ece-tools backup:list
   ```

   ```
   The list of backup files:
   app/etc/env.php
   app/etc/config.php
   ```

1. Stellen Sie die Konfigurationsdateien wieder her.

   ```
   ./vendor/bin/ece-tools backup:restore
   ```

   Sie erhalten eine Liste der vorhandenen Konfigurationsdateien, die von der Wiederherstellung betroffen sind.

   ```
   app/etc/env.php file exists! If you want to rewrite existed files use --force
   app/etc/config.php file exists! If you want to rewrite existed files use --force
   ```

1. Verwenden Sie die Option `--force` , um alle Dateien zu überschreiben.

   ```
   ./vendor/bin/ece-tools backup:restore --force
   ```

   ```
   Command backup:restore with option --force will rewrite your existed files. Do you want to continue [y/N]?y
   Backup file app/etc/env.php was restored.
   Backup file app/etc/config.php was restored.
   ```

1. Optional können Sie eine bestimmte Konfigurationsdatei wiederherstellen.

   ```
   ./vendor/bin/ece-tools backup:restore --force --file=app/etc/config.php
   ```

   ```
   Command backup:restore with option --force will rewrite your existed files. Do you want to continue [y/N]?y
   Backup file app/etc/config.php was restored.
   ```
