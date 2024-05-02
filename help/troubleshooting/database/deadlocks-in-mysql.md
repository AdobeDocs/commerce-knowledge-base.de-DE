---
title: Deadlocks in MySQL
description: In diesem Artikel wird über Deadlocks in MySQL gesprochen, die helfen, sie zu identifizieren und zu beheben, wenn sie eine Site herunterfahren, den Import von Datenbanken blockieren oder andere Adobe Commerce-Probleme verursachen.
exl-id: 529d1c0b-77f3-4604-9878-e7ea2c9c3640
feature: Best Practices, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Deadlocks in MySQL

In diesem Artikel wird über Deadlocks in MySQL gesprochen, die helfen, sie zu identifizieren und zu beheben, wenn sie eine Site herunterfahren, den Import von Datenbanken blockieren oder andere Adobe Commerce-Probleme verursachen.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.2.x und 2.3.x
* Adobe Commerce auf Cloud-Infrastruktur 2.2.x und 2.3.x

## Problem

Deadlocks in MySQL treten auf, wenn sich zwei oder mehr Transaktionen gegenseitig halten und Sperren anfordern. Deadlocks weisen nicht immer auf ein Problem hin, sind aber oft Symptom eines anderen MySQL- oder Adobe Commerce-Problems, das aufgetreten ist.

Häufig wird in den Anwendungs-, Bereitstellungs- oder MySQL-Protokollen eine *&quot;Deadlock&quot;* Fehler oder Fehler *&quot;Deadlock gefunden, wenn versucht wird, Sperrung zu erhalten; versuchen Sie, die Transaktion neu zu starten.&quot;*

## Ursache

Deadlocks können mehrere Ursachen haben. Am häufigsten ist es jedoch, wenn Sie eine Interaktion (Website/Prozesse/Cron-Aufträge/andere Benutzer/MySQL-Wartung/MySQL-Importe) ausführen, während Sie gleichzeitig DML-/DDL-Abfragen durchführen.

Es empfiehlt sich beispielsweise, einen blockierten MySQL-Datenbankimport zu vermeiden, indem Sie Ihre Site zunächst in den Wartungsmodus versetzen, um zu verhindern, dass SQL-Anforderungen in die Datenbank aufgenommen werden, die zu Deadlocks und einem blockierten Datenbankimport führen könnten.

## Lösung

1. Überprüfen Sie Ihre Anwendungs-, Bereitstellungs- oder MySQL-Protokolle auf Deadlock-Fehler:
   * [Protokollspeicherorte für Adobe Commerce und Magento Open Source](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/enable-logging.html)
   * [Adobe Commerce auf Cloud-Infrastrukturprotokollen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)
1. Überprüfen Sie Ihre MySQL-Prozessliste auf die Ausführung von Prozessen mit dem Befehl . `mysql -e 'show full processlist';`
1. Überprüfen Sie in Adobe Commerce in der Cloud-Infrastruktur, ob MySQL Slave aktiviert ist. Lesen Sie diesen Artikel: [Bereitstellen von Variablen (MYSQL\_USE\_SLAVE\_CONNECTION)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection).
1. Je nach den involvierten Fehlern kann die Lösung selbst vorhanden sein, oder Sie müssen ggf. Ihre hilfreichen Protokollinformationen einschließen, wenn Sie eine [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Verwandtes Lesen

* [Minimieren und Behandeln von Deadlocks](https://dev.mysql.com/doc/refman/5.7/en/innodb-deadlocks-handling.html)
* [Indexer-Optimierung - Indexer-Tabellenumschalter](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/)
* [Massenvorgänge - Nachrichten verarbeiten](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

>[!NOTE]
>
>Wir wissen, dass dieser Artikel immer noch branchenübliche Softwarebegriffe enthalten kann, die einige rassistisch, sexistisch oder unterdrückend finden und die den Leser verletzen, traumatisiert oder unerwünscht machen können. Adobe arbeitet daran, diese Begriffe aus unserem Code, unserer Dokumentation und unseren Benutzererlebnissen zu entfernen.
