---
title: Während der Installation, Ausnahme SessionHandler::read()
description: "Dieser Artikel enthält eine Fehlerbehebung für einen Ausnahmefehler **SessionHandler::read()** während der Adobe Commerce-Installation."
source-git-commit: 5cec04f8c4f80d34fc26b06eb929960ce21e2dc0
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# Während der Installation, Ausnahme SessionHandler::read()

In diesem Artikel wird eine Ausnahme korrigiert **SessionHandler::read()** Fehler während der Installation von Adobe Commerce.

## Problem

Beim letzten Schritt der Installation von Adobe Commerce wird die folgende Ausnahme angezeigt:

```temrinal
exception 'Exception' with message 'Warning: SessionHandler::read():
open(..) failed: No such file or directory (2) ../magento2/lib/internal/Magento/Framework/Session/SaveHandler.php on line 74'
in ../magento2/lib/internal/Magento/Framework/App/ErrorHandler.php:67
```

>[!NOTE]
>
>Dieser Fehler tritt nur in Codeversionen vor dem 28. September 2015 auf. Wenn Sie Code vom 29. September oder höher installieren, sollte dieser Fehler nicht auftreten. Weitere Informationen zu den Konfigurationsoptionen für Redis finden Sie unter [Konfigurieren von Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html) in unserer Entwicklerdokumentation. Weitere Informationen zum Festlegen von Redis mithilfe des Befehlszeilen-Installationsprogramms finden Sie in der [Installationsthema](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-install.html) oder [Bereitstellungskonfigurationsthema](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-deployment.html#instgde-cli-subcommands-configphp) in unserer Entwicklerdokumentation.

## Ursache

Dies geschieht, wenn Ihre `session.save_handler` Der PHP-Parameter ist auf einen anderen Sitzungsspeicher als `files` (zum Beispiel: `redis`, `memcached`usw.). Das ist ein bekanntes Problem, an dessen Lösung wir arbeiten.

## Lösungen:

* Aktualisieren Sie Ihren Adobe Commerce-Code. Siehe Abschnitt [Installationshandbuch > Aktualisieren der Adobe Commerce-Software](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-uninstall.html#instgde-install-magento-update) in unserer Entwicklerdokumentation.
* Verwenden Sie die folgende Problemumgehung mit vorhandenem Code:

## Suchen `php.ini` {#locate-php-ini}

Suchen `php.ini` durch Eingabe des folgenden Befehls:

```php
php -i | grep "Loaded Configuration File"
```

Typische Orte sind:

* Ubuntu: `/etc/php5/cli/php.ini`
* CentOS: `/etc/php.ini`

## Workaround {#workaround}

1. Als Benutzer mit `root` Berechtigungen, öffnen `php.ini` in einem Texteditor.
1. Suchen `session.save_handler`
1. Legen Sie sie auf eine der folgenden Arten fest:
   * So kommentieren Sie es aus:

     ```php
     ;session.save_path = <path>
     ```

   * So legen Sie ihn auf einen Dateisystempfad fest:

     ```php
     session.save_handler = files
     ```
