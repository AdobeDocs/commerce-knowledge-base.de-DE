---
title: Probleme mit Composer-Plug-ins bei der Aktualisierung auf Adobe Commerce 2.4.4
description: Dieser Artikel bietet eine Lösung, um das Problem mit Composer-Plug-ins beim Aktualisieren von Adobe Commerce 2.4.3 und früher auf Adobe Commerce 2.4.4 oder höher zu vermeiden (wenn zukünftige Versionen veröffentlicht werden).
exl-id: 7502ca9e-c307-4e8a-aa1d-4886e7be25da
feature: Upgrade
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# Probleme mit Composer-Plug-ins bei der Aktualisierung auf Adobe Commerce 2.4.4

Dieser Artikel bietet eine Lösung, um Probleme mit Composer-Plug-ins beim Upgrade von Adobe Commerce 2.4.3 und früher auf Adobe Commerce 2.4.4 oder höher zu vermeiden (wenn zukünftige Versionen veröffentlicht werden).

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort, jede Version bei Aktualisierung auf 2.4.4 oder höher (bei Veröffentlichung)
* Adobe Commerce in der Cloud-Infrastruktur, alle Versionen beim Aktualisieren auf 2.4.4 oder höher (bei Veröffentlichung)
* Magento Open Source, alle Versionen beim Aktualisieren auf 2.4.4 oder höher (wenn veröffentlicht)

## Problem

Beim Aktualisieren auf Adobe Commerce 2.4.4 oder höher nach Juli 2022 erhalten Sie möglicherweise eine Warnung vom Composer bezüglich Plugins.

<u>Zu reproduzierende Schritte</u>:

Voraussetzungen: Adobe Commerce 2.4.3 oder früher ist installiert.

1. Starten Sie das Upgrade wie unter [Durchführen eines Upgrades](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html).
1. Führen Sie die `composer update` -Befehl zum Aktualisieren der Adobe Commerce-Anwendung.

<u>Erwartete Ergebnisse</u>:

Die Aktualisierung ist erfolgreich.

<u>Tatsächliche Ergebnisse</u>:

Die Installation schlägt mit einem Fehler ähnlich dem folgenden fehl:

```bash
Writing lock file
Installing dependencies from lock file (including require-dev)
Package operations: 591 installs, 0 updates, 0 removals
  - Installing laminas/laminas-dependency-plugin (2.2.0): Extracting archive
laminas/laminas-dependency-plugin contains a Composer plugin which is currently not in your allow-plugins config. See https://getcomposer.org/allow-plugins
Do you trust "laminas/laminas-dependency-plugin" to execute code and wish to enable it now? (writes "allow-plugins" to composer.json) [y,n,d,?] y
Plugin initialization failed (require(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory), uninstalling plugin
  - Removing laminas/laminas-dependency-plugin (2.2.0)
    Install of laminas/laminas-dependency-plugin failed


  [ErrorException]
  require(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## Ursache

Ab Juli 2022 ändert der Composer den Standardwert der [`allow-plugins` option](https://getcomposer.org/doc/06-config.md#allow-plugins) nach `{}` und -Plug-ins werden nicht mehr geladen, es sei denn, dies ist zulässig.

## Lösung

Fügen Sie Folgendes zu Ihrer `composer.json` -Datei, je nachdem, wie Sie Adobe Commerce installiert haben:

* Wenn das Projekt erstellt wurde [mithilfe der `composer create-project` command](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html#get-the-metapackage):

  ```json
  "config": {
      "allow-plugins": {
          "dealerdirect/phpcodesniffer-composer-installer": true,
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

* Wenn das Projekt auf andere Weise erstellt wurde und nicht `"dealerdirect/phpcodesniffer-installer"` in `"require-dev"` Abschnitt:

  ```json
  "config": {
      "allow-plugins": {
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

Nach dem Aktualisieren der `composer.json` -Datei, führen Sie die `composer update` und starten Sie den Aktualisierungsprozess neu.
