---
title: Fehlende oder geänderte Konfigurationsdatei
description: Beheben Sie das Problem mit fehlender oder geänderter Konfigurationsdatei für Adobe Commerce.
exl-id: d80bf981-8ba6-4357-a841-57bf5d3f2a3f
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# Fehlende oder geänderte Konfigurationsdatei

In diesem Artikel wird beschrieben, wie Sie das Problem lösen können, bei dem Ihre Konfigurationsdateien geändert wurden oder fehlen.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle Versionen

## Problem

Konfigurationsdateien `config.php` und/oder `env.php` wurden falsch geändert oder fehlen.

## Lösung

Der Bereitstellungsprozess erstellt eine Sicherungsdatei für jede Konfigurationsdatei:

* `app/etc/config.php.bak` - enthält systemspezifische Einstellungen und wird während des Builds automatisch generiert, wenn sie nicht vorhanden ist
* `app/etc/env.php.bak` - enthält vertrauliche Konfigurationsdaten

Sie können sie mithilfe des Befehls ECE-Tools `backup:restore` wiederherstellen.

Die BAK-Dateien sind ein Produkt des Implementierungsprozesses. Wenn Sie eine Konfigurationsdatei nach der Bereitstellung manuell ändern, werden Ihre Änderungen nicht in den vorhandenen BAK-Dateien übernommen.

Wiederherstellen der Konfigurationsdateien:

1. Melden Sie sich mit [SSH](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) bei Ihrem Remote-Repository an.
1. Geben Sie die verfügbaren Backup-Dateien an.

   ```
   ./vendor/bin/ece-tools backup:list
   ```

   ```
   The list of backup files:
   app/etc/env.php
   app/etc/config.php
   ```

1. Wiederherstellen der Konfigurationsdateien.

   ```
   ./vendor/bin/ece-tools backup:restore
   ```

   Sie erhalten eine Liste der vorhandenen Konfigurationsdateien, die von der Wiederherstellung betroffen sind.

   ```
   app/etc/env.php file exists! If you want to rewrite existed files use --force
   app/etc/config.php file exists! If you want to rewrite existed files use --force
   ```

1. Verwenden Sie die Option &quot;`--force`&quot;, um alle Dateien zu überschreiben.

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
