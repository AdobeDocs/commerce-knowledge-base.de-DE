---
title: Beheben eines Fehlers bei einem illegalen Offset
description: Dieser Artikel bietet eine Lösung für den Fall, dass in Adobe Commerce 2.1 oder höher beim Erstellen eines neuen Produkts in Commerce Admin der Fehler „Illegalen Offset beheben“ angezeigt wird.
exl-id: 62d16d3c-7f4b-45e9-ae4b-fe2b58cc3620
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Beheben eines Fehlers bei einem illegalen Offset

Dieser Artikel bietet eine Lösung für den Fall, dass in Adobe Commerce 2.1 oder höher beim Erstellen eines neuen Produkts in Commerce Admin der Fehler „Illegalen Offset beheben“ angezeigt wird.

Wenn Sie in Adobe Commerce 2.1 oder höher ein neues Produkt in Commerce Admin erstellen, wird möglicherweise der folgende Fehler angezeigt:

```text
Warning: Illegal string offset 'is_in_stock' in [...]/vendor/
magento/module-catalog-inventory/Ui/DataProvider/Product/Form/
Modifier/AdvancedInventory.php on line 87
```

## Detail

Adobe Commerce 2.1 und höher verwenden PHP-Codekommentare im `getDocComment` Validierungsaufruf in der [`getExtensionAttributes`](https://github.com/magento/magento2/blob/2.3/lib/internal/Magento/Framework/Api/ExtensionAttributesFactory.php#L64-L73) in `Magento\Framework\Api\ExtensionAttributesFactory.php`.

Wenn Sie PHP OPcache aktiviert haben (was wir empfehlen), wird dieser Fehler angezeigt, da die OPcache Einstellung [`opcache.save_comments`](http://php.net/manual/en/opcache.configuration.php#ini.opcache.save_comments) standardmäßig deaktiviert ist.

## Abhilfe

Suchen Sie zum Beheben des Problems Ihre OPcache-Konfigurationseinstellungen und aktivieren Sie `opcache.save_comments` wie folgt:

### Schritt 1: Suchen Sie Ihre OP-Cache-Konfiguration

#### So suchen Sie nach OPcache-Konfigurationseinstellungen:

PHP OPcache-Einstellungen befinden sich normalerweise entweder in `php.ini` oder `opcache.ini`. Der Speicherort hängt möglicherweise von Ihrem Betriebssystem und der PHP-Version ab. Die OPcache-Konfigurationsdatei kann einen `[opcache]` Abschnitt oder Einstellungen wie `opcache.enable` aufweisen.

Verwenden Sie die folgenden Richtlinien, um sie zu finden:

* Apache-Webserver:<br>

Bei Ubuntu mit Apache befinden sich die OPcache-Einstellungen normalerweise in `php.ini`.<br>
Bei CentOS mit Apache oder Nginx befinden sich die OPcache-Einstellungen normalerweise in `/etc/php.d/opcache.ini`.<br>
Wenn nicht, verwenden Sie den folgenden Befehl, um sie zu finden:

```bash
    $ sudo find / -name 'opcache.ini'
```

* nginx-Webserver mit PHP-FPM: `/etc/php5/fpm/php.ini`.

Wenn Sie mehr als ein `opcache.ini` haben, ändern Sie alle.


### Schritt 2: `opcache.save_comments` aktivieren

1. Öffnen Sie Ihre OP-Cache-Konfigurationsdatei in einem Texteditor.
1. Suchen Sie `opcache.save_comments` und heben Sie ggf. die Auskommentierung auf.
1. Stellen Sie sicher, dass der Wert auf `1` gesetzt ist.
1. Speichern Sie Ihre Änderungen und beenden Sie den Texteditor.
1. Starten Sie den Webserver neu:

   * Apache, Ubuntu: `service apache2 restart`
   * Apache, CentOS: `service httpd restart`
   * nginx, Ubuntu und CentOS: `service nginx restart`

1. Generieren Sie die ID-Konfiguration und alle fehlenden Klassen neu, die automatisch generiert werden können:

```bash
    $ bin/magento setup:di:compile`
```
