---
title: Häufige Fehler und Lösungen bei PHP
description: In diesem Artikel werden einige häufige PHP Fatal Error-Schnellbeispiele aufgelistet, die Sie beim Durchsuchen Ihrer Adobe Commerce-Protokolle und der Lösungen für Probleme finden können, auf die sie hinweisen.
exl-id: 3e42d38f-97bc-4d38-8e36-23b1453f81d9
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Häufige Fehler und Lösungen bei PHP

In diesem Artikel werden einige häufige PHP Fatal Error-Schnellbeispiele aufgelistet, die Sie beim Durchsuchen Ihrer Adobe Commerce-Protokolle und der Lösungen für Probleme finden können, auf die sie hinweisen.

## Beispiel

*&#39;PHP Fatal error: Maximale Ausführungszeit von 60 Sekunden überschritten in ...&#39;*

## Lösung

Sie können die maximale Ausführungszeit aktualisieren, indem Sie eine benutzerdefinierte `max_execution_time` -Wert in `php.ini` Datei und erneute Bereitstellung.

Beispiel:

`max_execution_time = 120`

Lesen Sie die [php.ini-Einstellungen anpassen](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html) Artikel.

## Beispiel

*&#39;PHP Fatal error: Allowed memory size of 792723456 bytes erschöpft&#39;* (Das ist nur eine Beispiel-Byte-Größe.)

## Lösung

Anpassen Ihrer `php.ini` -Einstellungen. Lesen Sie hierzu [php.ini-Einstellungen anpassen](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html) Artikel.

## Beispiel

*&#39;PHP-Warnung: Unbekannt: Stream konnte nicht geöffnet werden: Keine solche Datei oder Verzeichnis.&#39;*

## Lösung

Stellen Sie sicher, dass Sie die Windows-Stilendungen nicht im `php.ini` -Datei. Unter Windows werden Zeilenende mit einer Kombination aus einem Wagenrücklauf (ASCII 0x0d oder \r) und einem Zeilenumbruch (\n) beendet, der auch als CR/LF bezeichnet wird.

## Beispiel

*&#39;PHP Fatal error: Uncaught PDOException: SQLSTATE\[HY000\] \[1040\] Zu viele Verbindungen in&#39;*

## Lösung

Der MySQL-Umgebung ist der Speicherplatz ausgegangen. Stellen Sie mehr Speicherplatz für die MySQL-Umgebung bereit.

## Beispiel

*&#39;PHP Fatal error: Uncaught TypeError: Return value of Magento&#39;*

## Lösung

Überprüfen Sie die `<root>/tmp` Verzeichnis, da es wahrscheinlich voll ist. Wenn es voll ist, geben Sie mehr Speicherplatz im Verzeichnis an. Dazu kann es gehören, einfach Dateien in ein anderes Verzeichnis zu verschieben oder sie zu löschen.

## Verwandtes Lesen

In unserer Entwicklerdokumentation:

* [Fehler bei PHP-Einstellungen](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html)
* [Erforderliche PHP-Einstellungen](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html)
* [Rediw-Überprüfung](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify)
* [Konfigurieren von Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html)
* [Fehler bei PHP-Speicherbegrenzung](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html#trouble-php-memory)
* [Lösungen für häufige Probleme - Speicherbegrenzung](https://devdocs.magento.com/guides/v2.3/test/unit/unit_test_execution_cli.html#solutions-to-common-problems)
