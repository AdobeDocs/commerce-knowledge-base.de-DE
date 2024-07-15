---
title: ECE-Tools und Patch-Update-Fehler Adobe Commerce Cloud-Infrastruktur 2.2.x, 2.3.x
description: Dieser Artikel bietet eine Lösung für das Problem, dass Fehlermeldungen wie "*failed to open stream:*"oder "*No such file or directory*"angezeigt werden, wenn Sie versuchen, Updates für ECE-Tools, Patches oder andere Änderungen bereitzustellen.
exl-id: b1658001-0ffd-4f8a-a15f-d785efcee51f
feature: Cloud, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# ECE-Tools und Patch-Update-Fehler Adobe Commerce Cloud-Infrastruktur 2.2.x, 2.3.x

Dieser Artikel bietet eine Lösung für das Problem, dass Fehlermeldungen wie &quot;*failed to open stream:*&quot;oder &quot;*No such file or directory*&quot;angezeigt werden, wenn Sie versuchen, Updates für ECE-Tools, Patches oder andere Änderungen bereitzustellen.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x

## Problem

Fehler bei der Bereitstellung von Updates für ECE-Tools, Patches oder andere Änderungen umfassen: PHP-Fehler in der Cloud-Konsole und im `var/log/cloud.log`

```
W: PHP Warning: require(<path to file>): failed to open stream: No such file or directory in <path to file> on line 70
W: PHP Fatal error: require(): Failed opening required '<path to file>;'
(include_path='<path to file>') in <path to file> on line 70

Warning: require(/app/vendor/composer/../../app/etc/NonComposerComponentRegistration.php):
failed to open stream: No such file or directory in /app/vendor/composer/autoload_real.php
on line 70

Fatal error: require(): Failed opening required '/app/vendor/composer/../../app/etc/NonComposerComponentRegistration.php'
(include_path='/app/vendor/magento/zendframework1/library:.:/usr/share/php')
in /app/vendor/composer/autoload_real.php on line 70

E: Error building project: Step failed with status code 255.
```

Fehler im Ausnahmeprotokoll:

```
CRITICAL:
error: <path to missing file>: No such file or directory
```

```
W: Generating optimized autoload files
W: PHP Warning: Uncaught ErrorException: require(<path to file>):
failed to open stream: No such file or directory in <path to file>
```

```
PHP Warning: Uncaught Exception: Warning: require(/app/setup/config/application.config.php):
failed to open stream: No such file or directory in /app/vendor/magento/framework/Console/Cli.php
on line 63 in /app/vendor/magento/framework/App/ErrorHandler.php:61
```

```
[Symfony\Component\Console\Exception\CommandNotFoundException]
 W: There are no commands defined in the "module" namespace.
```

## Ursache

Fehlkonfiguration Ihrer `composer.json` -Datei.

## Lösung

Wenn in Ihrer `composer.json` -Datei eine Einstellung fehlt, werden einige Verzeichnisse nicht aus der Adobe Commerce-Codebasis kopiert. Das Paket und das Update/Patch können nicht angewendet werden, da Dateien nicht gefunden werden.

Bitte ändern Sie Ihren zusätzlichen Abschnitt entsprechend dem unten angegebenen Abschnitt und versuchen Sie die Bereitstellung erneut.

```
"extra":{
  "magento-force": true,
  "magento-deploystrategy": "copy"
}
```

## Verwandtes Lesen

* [Upgrades und Patches](https://devdocs.magento.com/guides/v2.3/cloud/project/project-upgrade-parent.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=update%20ece%20tools) in unserer Entwicklerdokumentation.
