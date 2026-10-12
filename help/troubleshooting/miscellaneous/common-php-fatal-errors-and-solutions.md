---
title: Häufige schwerwiegende PHP Fehler und Lösungen
description: Dieser Artikel listet einige häufige Beispiele für schwerwiegende PHP-Fehler auf, die Sie beim Durchsuchen Ihrer Adobe Commerce-Protokolle finden konnten, sowie die Lösungen für Probleme, auf die sie hinweisen.
exl-id: 3e42d38f-97bc-4d38-8e36-23b1453f81d9
feature: Support
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: a59f76dc-e003-5617-951e-dffa5bd3de81
    internal-label: Support
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%
---
# Häufige schwerwiegende PHP Fehler und Lösungen

Dieser Artikel listet einige häufige Beispiele für schwerwiegende PHP-Fehler auf, die Sie beim Durchsuchen Ihrer Adobe Commerce-Protokolle finden konnten, sowie die Lösungen für Probleme, auf die sie hinweisen.

## Beispiel

Schwerwiegender Fehler bei *&#39;PHP: Maximale Ausführungszeit von 60 Sekunden überschritten in….&#39;*

## Lösung

Sie können die maximale Ausführungszeit aktualisieren, indem Sie einen benutzerdefinierten `max_execution_time` in Ihrer `php.ini` festlegen und erneut bereitstellen.

Beispiel:

`max_execution_time = 120`

Lesen Sie den Artikel [Anpassen der php.ini](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/app/php-settings)Einstellungen.

## Beispiel

*&#39;Schwerwiegender PHP-Fehler: Zulässige Speichergröße von 792723456 Bytes erschöpft&#39;* (Das ist nur eine Beispiel-Byte-Größe.)

## Lösung

`php.ini` anpassen. Lesen Sie diesen [Anpassen der php.ini-Einstellungen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/app/php-settings).

## Beispiel

*&#39;PHP Warning: Unknown: failed to open stream: No such file or directory&#39;*

## Lösung

Stellen Sie sicher, dass Sie die Windows-ähnlichen Endungen in der `php.ini`-Datei nicht entfernen. Unter Windows werden Zeilenenden durch eine Kombination aus Wagenrücklauf (ASCII 0x0d oder \r) und Zeilenumbruch (\n), auch CR/LF genannt, beendet.

## Beispiel

*&#39;Schwerwiegender PHP-Fehler: Nicht abgefangener PDOException: SQLSTATE\[HY000\] \[1040\] Zu viele Verbindungen in&#39;*

## Lösung

Der MySQL-Umgebung ist der Speicherplatz ausgegangen. Stellen Sie mehr Speicherplatz für die MySQL-Umgebung bereit.

## Beispiel

*&#39;PHP Schwerwiegender Fehler: Nicht abgefangener TypFehler: Rückgabewert von Magento&#39;*

## Lösung

Überprüfen Sie das `<root>/tmp` Verzeichnis, da es wahrscheinlich voll ist. Wenn er voll ist, geben Sie mehr Speicherplatz im Verzeichnis an. Dies kann bedeuten, dass Dateien einfach in ein anderes Verzeichnis verschoben oder gelöscht werden.

## Verwandtes Lesen

In unserer Entwicklerdokumentation:

* [PHP-Einstellungsfehler](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/overview)
* [Erforderliche PHP-Einstellungen](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/prerequisites/php-settings)
* [Redis-Überprüfung](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cache/redis/redis-session#verify-redis-connection)
* [Konfigurieren von Redis](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cache/redis/config-redis)
* [PHP-Speicherbegrenzungsfehler](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/overview)
* [Lösungen für häufige Probleme - Speicherlimit](https://developer.adobe.com/commerce/testing/guide/unit/command-line#solutions-to-common-problems)
