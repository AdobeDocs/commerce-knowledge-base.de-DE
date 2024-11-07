---
title: Fehler bei PHP-Einstellungen
description: Dieser Artikel bietet Lösungen für Fehler bei PHP-Einstellungen.
exl-id: 51fb3c95-2e25-4d86-a6cf-e08e90d097ca
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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
1. Suchen Sie die Datei &quot;`php.ini`&quot;mit dem folgenden Befehl:

   ```
   bash    $ php --ini
   ```

1. Verwenden Sie als Benutzer mit `root` -Berechtigungen einen Texteditor, um die von `Loaded Configuration File` angegebene `php.ini` zu öffnen.
1. Suchen Sie `memory_limit`.
1. Ändern Sie ihn für die normale Verwendung und das Debugging in den Wert `2GB` .
1. Speichern Sie Ihre Änderungen in `php.ini` und beenden Sie den Texteditor.
1. Starten Sie den Webserver neu. Beispiele:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`
   * nginx (sowohl CentOS als auch Ubuntu): `service nginx restart`

1. Versuchen Sie die Installation erneut.

## max-input-vars-Fehler aufgrund großer Formulare

Konfigurationen mit einer großen Anzahl von Storeviews, Produkten, Attributen oder Optionen können Formulare generieren, die die voreingestellte PHP-Grenze überschreiten. Wenn die Anzahl der gesendeten Werte die innerhalb von `php.ini` festgelegte Grenze von `max-input-vars` überschreitet (Standard ist 1000), werden die verbleibenden Daten nicht übertragen und diese Datenbankwerte werden nicht aktualisiert. Wenn dies eintritt, erscheint ein Warnhinweis im PHP-Protokoll:

```bash
PHP message: PHP Warning: Unknown: Input variables exceeded 1000. To increase the limit change max_input_vars in php.ini.
```

Es gibt keinen &quot;richtigen&quot;Wert für `max-input-vars`; er hängt von der Größe und Komplexität Ihrer Konfiguration ab. Ändern Sie den Wert in der Datei `php.ini` nach Bedarf. Siehe [Erforderliche PHP-Einstellungen](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings).

## xdebug maximum function nesting level error

Siehe [Während der Installation Fehler xdebug maximum function nesting level error](/help/troubleshooting/miscellaneous/installation-xdebug-maximum-function-nesting-level-error.md).

## Beim Zugriff auf eine PHTML-Vorlage werden Fehler angezeigt

Fehlertext ist normalerweise:

```bash
Parse error: syntax error, unexpected 'data' (T_STRING)
```

### Lösung: Legen Sie `asp_tags = off` in php.ini fest

Mehrere Vorlagen haben eine Syntax für die Unterstützung der abstrakten Ebene auf Vorlagen (verwenden Sie verschiedene Vorlagen-Engines wie Twig), die in `<% %>` -Tags eingeschlossen sind, wie diese [Vorlage](https://github.com/magento/magento2/blob/2.0/app/code/Magento/Catalog/view/adminhtml/templates/product/edit/base_image.phtml) zum Anzeigen eines Produktbilds:

```php
<img
    class="product-image"
    src="<%- data.url %>"
    data-position="<%- data.position %>"
    alt="<%- data.label %>" />
```

Weitere Informationen zu [asp\_tags](http://php.net/manual/en/ini.core.php#ini.asp-tags).

Bearbeiten Sie `php.ini` und legen Sie `asp_tags = off` fest. Weitere Informationen finden Sie unter [Erforderliche PHP-Einstellungen](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings).
