---
title: Die Installation hält bei etwa 70 % an
description: Dieser Artikel enthält eine Fehlerbehebung für , wenn die Installation bei etwa 70 % beendet wird.
exl-id: 04aa3572-3c42-4565-9f7f-b4d90df96df2
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Die Installation hält bei etwa 70 % an

Dieser Artikel enthält eine Fehlerbehebung für , wenn die Installation bei etwa 70 % beendet wird.

## Problem

Während der Installation mit dem Einrichtungs-Assistenten wird der Prozess bei etwa 70 % beendet (mit oder ohne Beispieldaten). Auf dem Bildschirm werden keine Fehler angezeigt.

## Ursache

Häufige Ursachen für dieses Problem sind:

* Die PHP-Einstellung für [`max_execution_time`](http://php.net/manual/en/info.configuration.php#ini.max-execution-time)
* Timeout-Werte für nginx und Varnish

## Lösung:

Legen Sie alle folgenden Einstellungen wie gewünscht fest.

### Alle Webserver und Server verschwinden {#all-web-servers-and-varnish}

1. Suchen Sie Ihre `php.ini` mithilfe einer [`phpinfo.php`](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo) -Datei.
1. Als Benutzer mit `root` Berechtigungen, öffnen `php.ini` in einem Texteditor.
1. Suchen Sie die `max_execution_time` -Einstellung.
1. Ändern Sie den Wert in `18000` .
1. Speichern Sie Ihre Änderungen in `php.ini` und beenden Sie den Texteditor.
1. Starten Sie Apache neu:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

   Wenn Sie Nginx oder Varnish verwenden, fahren Sie mit den folgenden Abschnitten fort.

### nur nginx {#nginx-only}

Wenn Sie nginx verwenden, verwenden Sie unsere im Lieferumfang enthaltene `nginx.conf.sample` oder fügen Sie eine Timeout-Einstellungen in der nginx-Host-Konfigurationsdatei zur `location ~ ^/setup/index.php` wie folgt:

```php
location ~ ^/setup/index.php {
    .....................
    fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
}
```

Starten Sie nginx neu: `service nginx restart`

### Nur Varnisch {#varnish-only}

Wenn Sie Varnish verwenden, bearbeiten Sie `default.vcl` und fügen Sie dem `backend` Stanza wie folgt:

```php
backend default {
.....................
      .first_byte_timeout = 600s;
}
```

Starten Sie Varnish neu.

```php
service varnish restart
```
