---
title: MySQL-Server ist verschwunden​ Fehler in Adobe Commerce in der Cloud
description: In diesem Artikel wird über die Lösung des Problems gesprochen, dass Sie in der Datei „cron.log“ die Fehlermeldung „SQL Server hat sich entfernt“ erhalten. Es können eine Reihe von Symptomen auftreten, darunter Probleme beim Importieren von Bilddateien oder Bereitstellungsfehler.
exl-id: 14cb9a6d-6d25-4044-8f52-d65648c03431
feature: Cloud, Paas, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
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

1. Überprüfen Sie den aktuellen Timeout-Zeitraum für `default_socket_timeout`, indem Sie in der CLI ausführen:    ```    php -i |grep default_socket_timeout    ```
1. Erhöhen Sie die Variable `default_socket_timeout` je nach Zeitüberschreitungseinstellung auf die erwartete längstmögliche Laufzeit in der `/etc/platform/<project_name>/php.ini`. Es wird empfohlen, zwischen 10 und 15 Minuten einzustellen.
1. Übertragen Sie sie an GIT und stellen Sie sie erneut bereit.

## Verwandtes Lesen

* [Datenbank-Upload verliert Verbindung zu MySQL](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md)
* [Best Practices für Datenbanken für Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=de)
* [Häufigste Datenbankprobleme in Adobe Commerce auf Cloud-Infrastrukturen](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html?lang=de)
