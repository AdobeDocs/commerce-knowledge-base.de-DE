---
title: Beheben eines unzulässigen Offset-Fehlers
description: Dieser Artikel bietet eine Lösung für den Fall, dass Sie in Adobe Commerce 2.1 oder höher beim Erstellen eines neuen Produkts in Commerce Admin einen unzulässigen Offset-Fehler beheben erhalten.
exl-id: 62d16d3c-7f4b-45e9-ae4b-fe2b58cc3620
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Beheben eines unzulässigen Offset-Fehlers

Dieser Artikel bietet eine Lösung für den Fall, dass Sie in Adobe Commerce 2.1 oder höher beim Erstellen eines neuen Produkts in Commerce Admin einen unzulässigen Offset-Fehler beheben erhalten.

In Adobe Commerce 2.1 oder höher wird beim Erstellen eines neuen Produkts in der Commerce Admin möglicherweise der folgende Fehler angezeigt:

```text
Warning: Illegal string offset 'is_in_stock' in [...]/vendor/
magento/module-catalog-inventory/Ui/DataProvider/Product/Form/
Modifier/AdvancedInventory.php on line 87
```

## Detail

Adobe Commerce 2.1 und höher verwenden PHP-Code-Kommentare in der `getDocComment` Überprüfungsaufruf in [`getExtensionAttributes`](https://github.com/magento/magento2/blob/2.3/lib/internal/Magento/Framework/Api/ExtensionAttributesFactory.php#L64-L73) -Methode in `Magento\Framework\Api\ExtensionAttributesFactory.php`.

Wenn Sie den PHP OPcache aktiviert haben (was wir empfehlen), wird dieser Fehler angezeigt, da standardmäßig die OPcache-Einstellung [`opcache.save_comments`](http://php.net/manual/en/opcache.configuration.php#ini.opcache.save_comments) deaktiviert ist.

## Workaround

Um das Problem zu beheben, suchen Sie Ihre OPcache-Konfigurationseinstellungen und aktivieren Sie `opcache.save_comments` wie folgt:

### Schritt 1: Suchen Sie Ihre OPcache-Konfiguration

#### So finden Sie die OPcache-Konfigurationseinstellungen:

PHP OPcache-Einstellungen befinden sich normalerweise entweder in `php.ini` oder `opcache.ini`. Der Speicherort kann von Ihrem Betriebssystem und Ihrer PHP-Version abhängen. Die OPcache-Konfigurationsdatei verfügt möglicherweise über eine `[opcache]` -Abschnitt oder Einstellungen wie `opcache.enable`.

Verwenden Sie die folgenden Richtlinien, um sie zu finden:

* Apache-Webserver:<br>

Für Ubuntu mit Apache befinden sich die OPcache-Einstellungen normalerweise in `php.ini`.<br>
Bei CentOS mit Apache oder nginx befinden sich die OPcache-Einstellungen normalerweise in `/etc/php.d/opcache.ini`.<br>
Wenn nicht, suchen Sie mit dem folgenden Befehl:

```bash
    $ sudo find / -name 'opcache.ini'
```

* nginx-Webserver mit PHP-FPM: `/etc/php5/fpm/php.ini`.

Wenn Sie mehr als eine `opcache.ini`, ändern Sie alle.


### Schritt 2: Aktivieren `opcache.save_comments`

1. Öffnen Sie die OPcache-Konfigurationsdatei in einem Texteditor.
1. Suchen `opcache.save_comments` und entfernen Sie gegebenenfalls die Kommentar.
1. Stellen Sie sicher, dass der Wert auf `1`.
1. Speichern Sie Ihre Änderungen und beenden Sie den Texteditor.
1. Starten Sie den Webserver neu:

   * Apache, Ubuntu: `service apache2 restart`
   * Apache, CentOS: `service httpd restart`
   * nginx, Ubuntu und CentOS: `service nginx restart`

1. Regenerieren Sie die ID-Konfiguration und alle fehlenden Klassen, die automatisch generiert werden können:

```bash
    $ bin/magento setup:di:compile`
```
