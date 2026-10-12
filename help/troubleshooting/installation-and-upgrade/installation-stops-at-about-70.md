---
title: Installation stoppt bei ca. 70%
description: Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass die Installation bei etwa 70 % beendet wird.
exl-id: 04aa3572-3c42-4565-9f7f-b4d90df96df2
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '200'
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

1. Suchen Sie Ihr `php.ini` mithilfe einer [`phpinfo.php`](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/prerequisites/optional-software).
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
