---
title: PHP-Einstellungsfehler
description: Dieser Artikel bietet Lösungen für PHP-Einstellungsfehler.
exl-id: 51fb3c95-2e25-4d86-a6cf-e08e90d097ca
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# PHP-Einstellungsfehler

Dieser Artikel bietet Lösungen für PHP-Einstellungsfehler.

## PHP-Speicherbegrenzungsfehler

Die Readiness Checks stellen sicher, dass Sie mindestens 1 GB Speicher für PHP-Prozesse reserviert haben. Diese Einstellung sollte für die meisten Installationen ausreichend sein, einschließlich der Installation optionaler Beispieldaten. Wir empfehlen jedoch mindestens 2 GB für das Debugging.

So erhöhen Sie die PHP-Speicherbegrenzung:

1. Melden Sie sich beim Adobe Commerce-Server an.
1. Suchen Sie die `php.ini`-Datei mithilfe des folgenden Befehls:

   ```
   bash    $ php --ini
   ```

1. Benutzende mit `root` Berechtigungen können einen Texteditor verwenden, um die von `Loaded Configuration File` angegebenen `php.ini` zu öffnen.
1. Suchen Sie `memory_limit`.
1. Ändern Sie ihn für die normale Verwendung und das Debugging in den Wert `2GB` .
1. Speichern Sie Ihre Änderungen in `php.ini` und beenden Sie den Texteditor.
1. Starten Sie den Webserver neu. Es folgen Beispiele:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`
   * nginx (sowohl CentOS als auch Ubuntu): `service nginx restart`

1. Installation erneut versuchen.

## max-input-vars-Fehler aufgrund großer Formulare

Konfigurationen mit einer hohen Anzahl von Storeviews, Produkten, Attributen oder Optionen können Formulare erzeugen, die das voreingestellte PHP-Limit überschreiten. Wenn die Anzahl der gesendeten Werte das innerhalb von `php.ini` festgelegte `max-input-vars`-Limit überschreitet (der Standardwert ist 1.000), werden die verbleibenden Daten nicht übertragen und diese Datenbankwerte werden nicht aktualisiert. Wenn dies eintritt, erscheint eine Warnung im PHP-Protokoll:

```bash
PHP message: PHP Warning: Unknown: Input variables exceeded 1000. To increase the limit change max_input_vars in php.ini.
```

Es gibt keinen „richtigen“ Wert für `max-input-vars`. Dies hängt von der Größe und Komplexität Ihrer Konfiguration ab. Ändern Sie den Wert in der `php.ini` nach Bedarf. Siehe [Erforderliche PHP-](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings).

## XDEBUG-Fehler bei maximaler Verschachtelungsebene der Funktion

Siehe [Fehler bei der Installation, xdebug maximum function nesting level](/help/troubleshooting/miscellaneous/installation-xdebug-maximum-function-nesting-level-error.md).

## Beim Zugriff auf eine PHTML-Vorlage werden Fehler angezeigt

Fehlertext ist normalerweise:

```bash
Parse error: syntax error, unexpected 'data' (T_STRING)
```

### Lösung: `asp_tags = off` in php.ini setzen

Mehrere Vorlagen verfügen über eine Syntax für die Unterstützung auf abstrakter Ebene bei Vorlagen (verwenden Sie verschiedene Vorlagen-Engines wie Twig), die in `<% %>`-Tags wie diese [Vorlage](https://github.com/magento/magento2/blob/2.0/app/code/Magento/Catalog/view/adminhtml/templates/product/edit/base_image.phtml) für die Anzeige eines Produktbilds eingeschlossen sind:

```php
<img
    class="product-image"
    src="<%- data.url %>"
    data-position="<%- data.position %>"
    alt="<%- data.label %>" />
```

Weitere Informationen zu &quot;[\_tags](http://php.net/manual/en/ini.core.php#ini.asp-tags).

Bearbeiten Sie `php.ini` und legen Sie `asp_tags = off` fest. Weitere Informationen finden Sie unter [Erforderliche PHP-Einstellungen](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings).
