---
title: 'Ausnahme: SessionHandler::read()'
description: Dieser Artikel enthält eine Fehlerbehebung für einen Ausnahmefehler **SessionHandler::read()** während der Installation von Adobe Commerce.
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# Ausnahme: SessionHandler::read()

Dieser Artikel enthält eine Fehlerbehebung für einen Ausnahmefehler **SessionHandler::read()** während der Installation von Adobe Commerce.

## Problem

Beim letzten Schritt der Installation von Adobe Commerce wird die folgende Ausnahme angezeigt:

```temrinal
exception 'Exception' with message 'Warning: SessionHandler::read():
open(..) failed: No such file or directory (2) ../magento2/lib/internal/Magento/Framework/Session/SaveHandler.php on line 74'
in ../magento2/lib/internal/Magento/Framework/App/ErrorHandler.php:67
```

>[!NOTE]
>
>Dieser Fehler tritt nur in Code-Versionen vor dem 28. September 2015 auf. Wenn Sie Code vom 29. September oder später installieren, sollte dieser Fehler nicht auftreten. Weitere Informationen zu den Konfigurationsoptionen für Redis finden Sie unter [Konfigurieren von Redis](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cache/redis/config-redis) in unserer Entwicklerdokumentation. Weitere Informationen zum Festlegen von Redis mithilfe des Befehlszeilen-Installationsprogramms finden Sie unter [Installations-](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/advanced)) oder [Bereitstellungskonfigurations-](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/tutorials/deployment)) in der Entwicklerdokumentation.

## Ursache

Dies geschieht, wenn Ihr `session.save_handler` PHP-Parameter auf einen anderen Sitzungsspeicher als `files` gesetzt ist (z.B. `redis`, `memcached` usw.). Dies ist ein bekanntes Problem, an dessen Behebung wir arbeiten.

## Lösungen:

* Aktualisieren des Adobe Commerce-Codes Siehe [Installationshandbuch > Aktualisieren der Adobe Commerce-Software](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/tutorials/uninstall) in unserer Entwicklerdokumentation.
* Verwenden Sie die folgende Problemumgehung mit vorhandenem Code:

## `php.ini` suchen {#locate-php-ini}

Suchen Sie `php.ini` durch Eingabe des folgenden Befehls:

```php
php -i | grep "Loaded Configuration File"
```

Typische Standorte folgen:

* Ubuntu: `/etc/php5/cli/php.ini`
* CentOS: `/etc/php.ini`

## Abhilfe {#workaround}

1. Wenn Sie ein Benutzer mit `root` Berechtigungen sind, öffnen Sie `php.ini` in einem Texteditor.
1. `session.save_handler` suchen
1. Legen Sie sie auf eine der folgenden Arten fest:
   * So kommentieren Sie es aus:

     ```php
     ;session.save_path = <path>
     ```

   * So legen Sie einen Dateisystempfad fest:

     ```php
     session.save_handler = files
     ```
