---
title: ECE-Tools und Patch-Aktualisierungsfehler Adobe Commerce Cloud Infrastructure 2.2.x., 2.3.x
description: Dieser Artikel bietet eine Lösung für das Problem, bei dem Fehlermeldungen wie "*Fehler beim Öffnen des Streams:*" oder "*Keine solche Datei oder Verzeichnis*" angezeigt werden, wenn versucht wird, Aktualisierungen für ECE-Tools, Patches oder andere Änderungen bereitzustellen.
exl-id: b1658001-0ffd-4f8a-a15f-d785efcee51f
feature: Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# ECE-Tools und Patch-Aktualisierungsfehler Adobe Commerce Cloud Infrastructure 2.2.x., 2.3.x

Dieser Artikel bietet eine Lösung für das Problem, bei dem Fehlermeldungen wie &quot;*Fehler beim Öffnen von stream:*&quot; oder &quot;*Keine solche Datei oder derartiges Verzeichnis* beim Versuch angezeigt werden, Aktualisierungen für ECE-Tools, Patches oder andere Änderungen bereitzustellen.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x

## Problem

Fehler bei der Bereitstellung von Updates für ECE-Tools, Patches oder anderen Änderungen sind: PHP-Fehler in der Cloud-Konsole und in der `var/log/cloud.log`

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

Fehlerhafte Konfiguration der `composer.json`.

## Lösung

Wenn in der `composer.json`-Datei eine Einstellung fehlt, werden einige Verzeichnisse nicht aus der Adobe Commerce-Code-Basis kopiert. Das Paket und das Update/Patch können nicht angewendet werden, da keine Dateien gefunden werden.

Bitte den zusätzlichen Abschnitt an den unten angegebenen Abschnitt anpassen und die Bereitstellung erneut versuchen.

```
"extra":{
  "magento-force": true,
  "magento-deploystrategy": "copy"
}
```

## Verwandtes Lesen

* [Upgrades und Patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/best-practices) in unserer Entwicklerdokumentation.
