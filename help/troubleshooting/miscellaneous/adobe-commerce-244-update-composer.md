---
title: Composer-Plug-ins-Probleme beim Upgrade auf Adobe Commerce 2.4.4
description: Dieser Artikel bietet eine Lösung, um das Problem mit Composer-Plug-ins beim Upgrade von Adobe Commerce 2.4.3 und früher auf Adobe Commerce 2.4.4 oder höher (wenn zukünftige Versionen veröffentlicht werden) zu vermeiden.
exl-id: 7502ca9e-c307-4e8a-aa1d-4886e7be25da
feature: Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# Composer-Plug-ins-Probleme beim Upgrade auf Adobe Commerce 2.4.4

Dieser Artikel bietet eine Lösung, um Probleme mit Composer-Plug-ins beim Upgrade von Adobe Commerce 2.4.3 und früher auf Adobe Commerce 2.4.4 oder höher (wenn zukünftige Versionen veröffentlicht werden) zu vermeiden.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises, jede Version bei der Aktualisierung auf 2.4.4 oder höher (bei Veröffentlichung)
* Adobe Commerce auf Cloud-Infrastruktur, jede Version bei der Aktualisierung auf 2.4.4 oder höher (bei Veröffentlichung)
* Magento Open Source, jede Version bei der Aktualisierung auf 2.4.4 oder höher (bei Veröffentlichung)

## Problem

Bei der Aktualisierung auf Adobe Commerce 2.4.4 oder höher nach Juli 2022 erhalten Sie möglicherweise eine Warnung von Composer zu Plug-ins.

<u>Schritte zur Reproduktion</u>:

Voraussetzungen: Adobe Commerce 2.4.3 oder früher ist installiert.

1. Starten Sie das Upgrade wie unter [Durchführen eines Upgrades](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html) beschrieben.
1. Führen Sie den `composer update` Befehl aus, um die Adobe Commerce-Anwendung zu aktualisieren.

<u>Erwartete Ergebnisse</u>:

Upgrade ist erfolgreich.

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

Nach Juli 2022 ändert Composer den Standardwert der [`allow-plugins` Option ](https://getcomposer.org/doc/06-config.md#allow-plugins) in `{}` und Plug-ins werden nicht mehr geladen, es sei denn, sie sind erlaubt.

## Lösung

Fügen Sie je nach Installation von Adobe Commerce Folgendes zu Ihrer `composer.json` hinzu:

* Wenn das Projekt erstellt wurde [mit dem `composer create-project` Befehl](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer#get-the-metapackage):

  ```json
  "config": {
      "allow-plugins": {
          "dealerdirect/phpcodesniffer-composer-installer": true,
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

* Wenn das Projekt auf eine andere Weise erstellt wurde und in `"require-dev"` Abschnitt keine `"dealerdirect/phpcodesniffer-installer"` enthält:

  ```json
  "config": {
      "allow-plugins": {
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

Führen Sie nach dem Aktualisieren der `composer.json` den Befehl `composer update` aus und starten Sie den Aktualisierungsprozess neu.
