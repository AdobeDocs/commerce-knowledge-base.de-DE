---
title: Während der Installation, Ausnahme SessionHandler::read()
description: "Dieser Artikel enthält eine Fehlerbehebung für einen Ausnahmefehler **SessionHandler::read()** während der Adobe Commerce-Installation."
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# Während der Installation, Ausnahme SessionHandler::read()

Dieser Artikel enthält eine Fehlerbehebung für den Ausnahmefehler **SessionHandler::read()** während der Installation von Adobe Commerce.

## Problem

Beim letzten Schritt der Installation von Adobe Commerce wird die folgende Ausnahme angezeigt:

```temrinal
exception 'Exception' with message 'Warning: SessionHandler::read():
open(..) failed: No such file or directory (2) ../magento2/lib/internal/Magento/Framework/Session/SaveHandler.php on line 74'
in ../magento2/lib/internal/Magento/Framework/App/ErrorHandler.php:67
```

>[!NOTE]
>
>Dieser Fehler tritt nur in Codeversionen vor dem 28. September 2015 auf. Wenn Sie Code vom 29. September oder höher installieren, sollte dieser Fehler nicht auftreten. Weitere Informationen zu den Konfigurationsoptionen für Redis finden Sie unter [Konfigurieren von Redis](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/redis/config-redis) in unserer Entwicklerdokumentation. Weitere Informationen zum Angeben von Redis mithilfe des Befehlszeilen-Installationsprogramms finden Sie im [Installationsthema](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/advanced) oder im [Thema zur Bereitstellungskonfiguration](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/deployment) in unserer Entwicklerdokumentation.

## Ursache

Dies geschieht, wenn Ihr `session.save_handler` PHP-Parameter auf einen anderen Sitzungsspeicher als `files` gesetzt ist (z. B. `redis`, `memcached` usw.). Das ist ein bekanntes Problem, an dessen Lösung wir arbeiten.

## Lösungen:

* Aktualisieren Sie Ihren Adobe Commerce-Code. Weitere Informationen finden Sie in unserer Entwicklerdokumentation unter [Installationshandbuch > Aktualisieren der Adobe Commerce-Software](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall) .
* Verwenden Sie die folgende Problemumgehung mit vorhandenem Code:

## Suchen Sie `php.ini` {#locate-php-ini}

Suchen Sie `php.ini`, indem Sie den folgenden Befehl eingeben:

```php
php -i | grep "Loaded Configuration File"
```

Typische Orte sind:

* Ubuntu: `/etc/php5/cli/php.ini`
* CentOS: `/etc/php.ini`

## Workaround {#workaround}

1. Als Benutzer mit `root` -Berechtigungen öffnen Sie `php.ini` in einem Texteditor.
1. Suchen Sie `session.save_handler`
1. Legen Sie sie auf eine der folgenden Arten fest:
   * So kommentieren Sie es aus:

     ```php
     ;session.save_path = <path>
     ```

   * So legen Sie ihn auf einen Dateisystempfad fest:

     ```php
     session.save_handler = files
     ```
