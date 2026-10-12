---
title: MySQL-Server ist verschwunden​ Fehler in Adobe Commerce in der Cloud
description: In diesem Artikel wird über die Lösung des Problems gesprochen, dass Sie in der Datei „cron.log“ die Fehlermeldung „SQL Server hat sich entfernt“ erhalten. Es können eine Reihe von Symptomen auftreten, darunter Probleme beim Importieren von Bilddateien oder Bereitstellungsfehler.
exl-id: 14cb9a6d-6d25-4044-8f52-d65648c03431
feature: Cloud, Paas, Services, Variables
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
subfeature_v2:
  - id: 2191e157-828a-5358-ad69-ebcaa8402915
    internal-label: Variables
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%
---
# MySQL-Server ist verschwunden&#x200B; Fehler in Adobe Commerce in der Cloud

In diesem Artikel wird die Lösung des Problems beschrieben, dass Sie die Fehlermeldung &quot;*SQL Server ist verschwunden* &quot; in der `cron.log`-Datei erhalten. Es können eine Reihe von Symptomen auftreten, darunter Probleme beim Importieren von Bilddateien oder Bereitstellungsfehler.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle [unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problem

Sie erhalten die Fehlermeldung &quot;*SQL Server ist* &quot; in der `cron.log`.

<u>Schritte zur Reproduktion</u>

Importieren von Dateien und Trigger einer -Bereitstellung.

<u>Erwartetes Ergebnis</u>

Erfolgreiche Bereitstellung.

<u>Tatsächliches Ergebnis</u>

Fehlermeldung in `cron.log` :“ *SQLSTATE\[HY000\] \[2006\] Der MySQL-Server wurde entfernt at/app/AAAAAAAAA/vendor/magento/zendframework1/library/Zend/Db/Adapter/Pdo/Abstract.php:144“*

## Ursache

Der `default_socket_timeout` ist zu niedrig eingestellt. Dies wird durch die Einstellung `default_socket_timeout` verursacht. Wenn PHP innerhalb dieses Zeitraums nichts von der MySQL-Datenbank erhält, geht es davon aus, dass diese getrennt ist und gibt den Fehler aus.

## Lösung

1. Überprüfen Sie die aktuelle Zeitüberschreitungsdauer für `default_socket_timeout`, indem Sie in der CLI: `php -i |grep default_socket_timeout` ausführen.
1. Überprüfen Sie den aktuellen Timeout-Zeitraum für `default_socket_timeout`, indem Sie in der CLI ausführen: `php -i |grep default_socket_timeout`
1. Erhöhen Sie die Variable `default_socket_timeout` je nach Zeitüberschreitungseinstellung auf die erwartete längstmögliche Laufzeit in der `/etc/platform/<project_name>/php.ini`. Es wird empfohlen, zwischen 10 und 15 Minuten einzustellen.
1. Übertragen Sie sie an GIT und stellen Sie sie erneut bereit.

## Verwandtes Lesen

* [Best Practices für Datenbanken für Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=de)
* [Häufigste Datenbankprobleme in Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html?lang=de)
