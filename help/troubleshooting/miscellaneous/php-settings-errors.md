---
title: Fehler bei PHP-Einstellungen
description: Dieser Artikel bietet Lösungen für Fehler bei PHP-Einstellungen.
exl-id: 51fb3c95-2e25-4d86-a6cf-e08e90d097ca
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Fehler bei PHP-Einstellungen

Dieser Artikel bietet Lösungen für Fehler bei PHP-Einstellungen.

## Fehler bei PHP-Speicherbegrenzung

Die Readiness-Prüfungen stellen sicher, dass für PHP-Prozesse mindestens 1 GB Speicher zur Verfügung stehen. Diese Einstellung sollte für die meisten Installationen ausreichen, einschließlich der Installation optionaler Beispieldaten. Es wird jedoch empfohlen, mindestens 2 GB für das Debugging zu verwenden.

So erhöhen Sie die PHP-Speicherbegrenzung:

1. Melden Sie sich bei Ihrem Adobe Commerce-Server an.
1. Suchen Sie Ihre `php.ini` Datei mit dem folgenden Befehl:

   ```
   bash    $ php --ini
   ```

1. Als Benutzer mit `root` Berechtigungen verwenden Sie einen Texteditor zum Öffnen der `php.ini` festgelegt durch `Loaded Configuration File`.
1. Suchen `memory_limit`.
1. Ändern Sie ihn in den Wert von `2GB` für die normale Verwendung und das Debugging.
1. Speichern Sie Ihre Änderungen in `php.ini` und beenden Sie den Texteditor.
1. Starten Sie den Webserver neu. Beispiele:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`
   * nginx (sowohl CentOS als auch Ubuntu): `service nginx restart`

1. Versuchen Sie die Installation erneut.

## max-input-vars-Fehler aufgrund großer Formulare

Konfigurationen mit einer großen Anzahl von Storeviews, Produkten, Attributen oder Optionen können Formulare generieren, die die voreingestellte PHP-Grenze überschreiten. Wenn die Anzahl gesendeter Werte die `max-input-vars` innerhalb der `php.ini` (Standardwert ist 1000), werden die verbleibenden Daten nicht übertragen und diese Datenbankwerte werden nicht aktualisiert. Wenn dies eintritt, erscheint ein Warnhinweis im PHP-Protokoll:

```terminal
PHP message: PHP Warning: Unknown: Input variables exceeded 1000. To increase the limit change max_input_vars in php.ini.
```

Es gibt keinen &quot;richtigen&quot;Wert für `max-input-vars`; dies hängt von der Größe und Komplexität Ihrer Konfiguration ab. Ändern Sie den Wert im `php.ini` Datei nach Bedarf. Siehe [Erforderliche PHP-Einstellungen](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html).

## xdebug maximum function nesting level error

Siehe [Während der Installation Fehler der maximalen Funktionsverschachtelungsstufe xdebug](/help/troubleshooting/miscellaneous/installation-xdebug-maximum-function-nesting-level-error.md).

## Beim Zugriff auf eine PHTML-Vorlage werden Fehler angezeigt

Fehlertext ist normalerweise:

```terminal
Parse error: syntax error, unexpected 'data' (T_STRING)
```

### Lösung: Festlegen `asp_tags = off` in php.ini

Mehrere Vorlagen haben eine Syntax, um abstrakte Ebenen auf Vorlagen zu unterstützen (verwenden Sie verschiedene Vorlagen-Engines wie Twig), die in `<% %>` Tags wie diese [template](https://github.com/magento/magento2/blob/2.0/app/code/Magento/Catalog/view/adminhtml/templates/product/edit/base_image.phtml) zum Anzeigen eines Produktbilds:

```php
<img
    class="product-image"
    src="<%- data.url %>"
    data-position="<%- data.position %>"
    alt="<%- data.label %>" />
```

Weitere Informationen über [asp\_tags](http://php.net/manual/en/ini.core.php#ini.asp-tags).

Bearbeiten `php.ini` und `asp_tags = off`. Weitere Informationen finden Sie unter [Erforderliche PHP-Einstellungen](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html).
