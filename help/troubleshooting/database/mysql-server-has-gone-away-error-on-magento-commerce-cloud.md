---
title: Der MySQL-Server ist ​ Fehler auf Adobe Commerce in der Cloud verschwunden.
description: In diesem Artikel wird über die Lösung des Problems gesprochen, bei dem Sie eine Fehlermeldung erhalten, dass der SQL-Server verschwunden ist* in der Datei "cron.log". Es kann zu einer Reihe von Symptomen kommen, darunter Probleme beim Importieren von Bilddateien oder Bereitstellungsfehler.
exl-id: 14cb9a6d-6d25-4044-8f52-d65648c03431
feature: Cloud, Paas, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Der MySQL-Server ist &#x200B; Fehler auf Adobe Commerce in der Cloud verschwunden.

In diesem Artikel wird über die Lösung des Problems gesprochen, bei dem Sie eine &quot; *Der SQL-Server wurde entfernt* &quot; Fehlermeldung in der `cron.log` -Datei. Es kann zu einer Reihe von Symptomen kommen, darunter Probleme beim Importieren von Bilddateien oder Bereitstellungsfehler.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle [unterstützte Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problem

Sie erhalten eine &quot; *Der SQL-Server wurde entfernt* &quot; Fehlermeldung in der `cron.log` -Datei.

<u>Zu reproduzierende Schritte</u>

Importieren von Dateien und Trigger einer Bereitstellung.

<u>Erwartetes Ergebnis</u>

Erfolgreiche Implementierung.

<u>Tatsächliches Ergebnis</u>

Fehlermeldung in `cron.log` :&quot; *SQLSTATE\[HY000\] \[2006\] MySQL-Server wurde entfernt at/app/AAAAAAAAA/vendor/magento/zendframework1/library/Zend/Db/Adapter/Pdo/Abstract.php:144&quot;*

## Ursache

Die `default_socket_timeout` zu niedrig eingestellt ist. Dies wird durch die Einstellung `default_socket_timeout` . Wenn PHP innerhalb dieses Zeitraums von der MySQL-Datenbank nichts erhält, geht es davon aus, dass die Verbindung getrennt ist, und gibt den Fehler aus.

## Lösung

1. Überprüfen Sie den aktuellen Timeout-Zeitraum für `default_socket_timeout` durch Ausführen in der CLI:    ```    php -i |grep default_socket_timeout    ```
1. Je nach Timeout-Einstellung erhöht sich die `default_socket_timeout` zur erwarteten längsten Laufzeit in der `/etc/platform/<project_name>/php.ini` -Datei. Es wird empfohlen, zwischen 10 und 15 Minuten festzulegen.
1. Übertragen Sie sie auf GIT und stellen Sie sie erneut bereit.

## Verwandtes Lesen

* [Beim Hochladen der Datenbank wird die Verbindung zu MySQL unterbrochen](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md)
* [Best Practices für Datenbanken mit Adobe Commerce in Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
* [Häufigste Datenbankprobleme in Adobe Commerce bei der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html)
