---
title: Die Installation hält bei etwa 70 % an
description: Dieser Artikel enthält eine Fehlerbehebung für , wenn die Installation bei etwa 70 % beendet wird.
exl-id: 04aa3572-3c42-4565-9f7f-b4d90df96df2
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

1. Suchen Sie Ihre `php.ini` mithilfe einer [`phpinfo.php`](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software) -Datei.
1. Als Benutzer mit `root` -Berechtigungen öffnen Sie `php.ini` in einem Texteditor.
1. Suchen Sie die Einstellung &quot;`max_execution_time`&quot;.
1. Ändern Sie den Wert in `18000` .
1. Speichern Sie Ihre Änderungen in `php.ini` und beenden Sie den Texteditor.
1. Starten Sie Apache neu:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

   Wenn Sie Nginx oder Varnish verwenden, fahren Sie mit den folgenden Abschnitten fort.

### nur nginx {#nginx-only}

Wenn Sie nginx verwenden, verwenden Sie unseren eingeschlossenen `nginx.conf.sample` oder fügen Sie wie folgt in der nginx-Host-Konfigurationsdatei eine Zeitüberschreitungseinstellung zum Abschnitt `location ~ ^/setup/index.php` hinzu:

```php
location ~ ^/setup/index.php {
    .....................
    fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
}
```

Nginx neu starten: `service nginx restart`

### Nur Varnisch {#varnish-only}

Wenn Sie &quot;Varnish&quot;verwenden, bearbeiten Sie `default.vcl` und fügen Sie dem Stanza `backend` einen Timeout-Grenzwert wie folgt hinzu:

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
