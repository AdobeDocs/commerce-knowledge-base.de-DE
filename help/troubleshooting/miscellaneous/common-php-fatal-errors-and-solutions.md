---
title: Häufige Fehler und Lösungen bei PHP
description: In diesem Artikel werden einige häufige PHP Fatal Error-Schnellbeispiele aufgelistet, die Sie beim Durchsuchen Ihrer Adobe Commerce-Protokolle und der Lösungen für Probleme finden können, auf die sie hinweisen.
exl-id: 3e42d38f-97bc-4d38-8e36-23b1453f81d9
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Häufige Fehler und Lösungen bei PHP

In diesem Artikel werden einige häufige PHP Fatal Error-Schnellbeispiele aufgelistet, die Sie beim Durchsuchen Ihrer Adobe Commerce-Protokolle und der Lösungen für Probleme finden können, auf die sie hinweisen.

## Beispiel

*&#39;PHP Fatal error: Maximale Ausführungszeit von 60 Sekunden überschritten in ...&#39;*

## Lösung

Sie können die maximale Ausführungsdauer aktualisieren, indem Sie in Ihrer `php.ini` -Datei einen benutzerdefinierten `max_execution_time` -Wert festlegen und die Bereitstellung erneut vornehmen.

Beispiel:

`max_execution_time = 120`

Lesen Sie den Artikel [php.ini-Einstellungen anpassen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/php-settings) .

## Beispiel

*&#39;PHP Fatal error: Zulässige Speichergröße von 792723456 Byte erschöpft&#39;* (Dies ist nur eine Beispiel-Byte-Größe.)

## Lösung

Passen Sie Ihre `php.ini` -Einstellungen an. Lesen Sie diesen Artikel [php.ini-Einstellungen anpassen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/php-settings) .

## Beispiel

*&#39;PHP-Warnung: Unbekannt: Nicht bekannt: Fehler beim Öffnen des Streams: Keine solche Datei oder Verzeichnis&#39;*

## Lösung

Entfernen Sie nicht die Windows-Stilendungen in der Datei &quot;`php.ini`&quot;. Unter Windows werden Zeilenende mit einer Kombination aus einem Wagenrücklauf (ASCII 0x0d oder \r) und einem Zeilenumbruch (\n) beendet, der auch als CR/LF bezeichnet wird.

## Beispiel

*&#39;PHP Schwerwiegender Fehler: Uncaught PDOException: SQLSTATE\[HY000\] \[1040\] Zu viele Verbindungen in&#39;*

## Lösung

Der MySQL-Umgebung ist der Speicherplatz ausgegangen. Stellen Sie mehr Speicherplatz für die MySQL-Umgebung bereit.

## Beispiel

*&#39;PHP Fatal error: Uncaught TypeError: Return value of Magento&#39;*

## Lösung

Überprüfen Sie den Ordner &quot;`<root>/tmp`&quot;, da er wahrscheinlich voll ist. Wenn es voll ist, geben Sie mehr Speicherplatz im Verzeichnis an. Dazu kann es gehören, einfach Dateien in ein anderes Verzeichnis zu verschieben oder sie zu löschen.

## Verwandtes Lesen

In unserer Entwicklerdokumentation:

* [Fehler bei PHP-Einstellungen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/overview)
* [Erforderliche PHP-Einstellungen](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings)
* [Überprüfung der Umkehrung](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/redis/redis-session#verify-redis-connection)
* [Redis konfigurieren](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/redis/config-redis)
* [PHP-Speicherbegrenzungsfehler](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/overview)
* [Lösungen für häufige Probleme - Speicherbeschränkung](https://developer.adobe.com/commerce/testing/guide/unit/command-line/#solutions-to-common-problems)
