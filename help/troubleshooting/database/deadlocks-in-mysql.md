---
title: Deadlocks in MySQL
description: In diesem Artikel wird über Deadlocks in MySQL gesprochen, um sie zu identifizieren und zu beheben, wenn sie zu einem Ausfall einer Site, einem blockierten Datenbankimport oder anderen Adobe Commerce-Problemen führen.
exl-id: 529d1c0b-77f3-4604-9878-e7ea2c9c3640
feature: Best Practices, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Deadlocks in MySQL

In diesem Artikel wird über Deadlocks in MySQL gesprochen, um sie zu identifizieren und zu beheben, wenn sie zu einem Ausfall einer Site, einem blockierten Datenbankimport oder anderen Adobe Commerce-Problemen führen.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.2.x und 2.3.x
* Adobe Commerce auf Cloud-Infrastrukturen 2.2.x und 2.3.x

## Problem

Deadlocks in MySQL treten auf, wenn zwei oder mehr Transaktionen einander halten und Sperren anfordern. Deadlocks, die vorhanden sind, deuten nicht immer auf ein Problem hin, sind jedoch häufig ein Symptom für ein anderes MySQL- oder Adobe Commerce-Problem, das aufgetreten ist.

Häufig wird in den Anwendungs-, Bereitstellungs- oder MySQL-Protokollen ein *„Deadlock“*-Fehler oder der Fehler „Deadlock gefunden, *beim Versuch, eine Sperre zu erhalten, versucht wird, die Transaktion neu zu starten“*

## Ursache

Deadlocks können mehrere Ursachen haben, aber die häufigste ist, wenn Sie irgendeine Interaktion (Website/Prozesse/Cron-Aufträge/andere Benutzer/MySQL-Wartung/MySQL-Importe) durchführen, während Sie DML/DDL-Abfragen gleichzeitig ausführen.

Als Beispiel ist es eine Best Practice, einen blockierten MySQL-Datenbankimport zu vermeiden, indem Sie Ihre Site zunächst in den Wartungsmodus versetzen, um zu vermeiden, dass SQL-Anfragen an die Datenbank gesendet werden, die zu Deadlocks und einem blockierten Datenbankimport führen könnten.

## Lösung

1. Überprüfen Sie die Anwendungs-, Bereitstellungs- oder MySQL-Protokolle auf Deadlockfehler:
   * [Speicherorte für Adobe Commerce- und Magento Open Source-Protokolle](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/enable-logging.html)
   * [Speicherorte für Adobe Commerce in Cloud-Infrastrukturprotokollen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)
1. Überprüfen Sie mit dem Befehl `mysql -e 'show full processlist';` Ihre MySQL-Prozessliste auf laufende Prozesse
1. Wenn in Adobe Commerce in der Cloud-Infrastruktur, überprüfen Sie, ob MySQL-Slave aktiviert ist. Lesen Sie diesen Artikel: [Variablen bereitstellen (MYSQL\_USE\_SLAVE\_CONNECTION)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection).
1. Je nach den jeweiligen Fehlern kann sich die Lösung selbst präsentieren, oder Sie müssen Ihre hilfreichen Protokollinformationen angeben, wenn Sie ein „Support-Ticket[ öffnen ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Verwandtes Lesen

* [So minimieren und handhaben Sie Deadlocks](https://dev.mysql.com/doc/refman/5.7/en/innodb-deadlocks-handling.html)
* [Indexeroptimierung - Umschalten der Indexertabelle](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/)
* [Massenvorgänge - Verarbeiten von Nachrichten](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

>[!NOTE]
>
>Wir sind uns bewusst, dass dieser Artikel immer noch branchenübliche Softwarebegriffe enthalten kann, die manche als rassistisch, sexistisch oder repressiv empfinden und die den Leser verletzen, traumatisieren oder unwillkommen machen können. Adobe arbeitet daran, diese Begriffe aus unserem Code, unserer Dokumentation und unseren Benutzererlebnissen zu entfernen.
