---
title: Installation stoppt bei ca. 70%
description: Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass die Installation bei etwa 70 % beendet wird.
exl-id: 04aa3572-3c42-4565-9f7f-b4d90df96df2
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Installation stoppt bei ca. 70%

Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass die Installation bei etwa 70 % beendet wird.

## Problem

Während der Installation mithilfe des Setup-Assistenten stoppt der Vorgang bei etwa 70 % (mit oder ohne Beispieldaten). Auf dem Bildschirm werden keine Fehler angezeigt.

## Ursache

Häufige Ursachen für dieses Problem sind:

* Die PHP-Einstellung für [`max_execution_time`](http://php.net/manual/en/info.configuration.php#ini.max-execution-time)
* Zeitüberschreitungswerte für nginx und varnish

## Lösung:

Legen Sie alle folgenden Einstellungen wie gewünscht fest.

### Alle Webserver und Lackierung {#all-web-servers-and-varnish}

1. Suchen Sie Ihr `php.ini` mithilfe einer [`phpinfo.php`](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software).
1. Wenn Sie ein Benutzer mit `root` Berechtigungen sind, öffnen Sie `php.ini` in einem Texteditor.
1. Suchen Sie die `max_execution_time`.
1. Ändern Sie den Wert in `18000` .
1. Speichern Sie Ihre Änderungen in `php.ini` und beenden Sie den Texteditor.
1. Apache neu starten:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

   Wenn Sie nginx oder Lack verwenden, fahren Sie mit den folgenden Abschnitten fort.

### Nur nginx {#nginx-only}

Wenn Sie nginx verwenden, verwenden Sie unsere enthaltene `nginx.conf.sample` oder fügen Sie eine Zeitüberschreitungseinstellung in der Konfigurationsdatei des nginx-Hosts wie folgt zum Abschnitt `location ~ ^/setup/index.php` hinzu:

```php
location ~ ^/setup/index.php {
    .....................
    fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
}
```

Nginx neu starten: `service nginx restart`

### Nur lackieren {#varnish-only}

Wenn Sie „Varnish“ verwenden, bearbeiten Sie `default.vcl` und fügen Sie der `backend`-Strophe einen Timeout-Grenzwert wie folgt hinzu:

```php
backend default {
.....................
      .first_byte_timeout = 600s;
}
```

Lack neu starten.

```php
service varnish restart
```
