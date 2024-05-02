---
title: Datenbankfehler im Zusammenhang mit max_allowed_packet in Adobe Commerce
description: Dieser Artikel bietet eine Lösung für Fehler bei der Datenbankverbindung unter "var/log/exception.log", die beim Import einer großen Anzahl von Produkten oder bei der Ausführung einer anderen Aufgabe auftreten können, die den Server zwingt, größere Pakete als in "max_allowed_packet"festgelegt zu verarbeiten, die größer als der Standardwert (16 MB) sind.
exl-id: e8932b72-91a3-43ea-800e-a6c7a5a17656
feature: Best Practices, Observability, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Datenbankfehler im Zusammenhang mit max_allowed_packet in Adobe Commerce

Dieser Artikel bietet eine Lösung für Fehler bei der Datenbankverbindung in der `var/log/exception.log` die beim Import einer großen Anzahl von Produkten oder bei der Ausführung einer anderen Aufgabe auftreten können, die den Server zwingt, größere Pakete als in `max_allowed_packet` größer als der Standardwert ist, 16 MB.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort, alle [unterstützte Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Bei einem MySQL-Client oder dem [mysqld](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html) Server erhält ein Paket größer als [max\_allowed\_packet](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html#sysvar_max_allowed_packet) Byte, wird eine [ER\_NET\_PACKET\_TOO\_LARGE](https://dev.mysql.com/doc/mysql-errors/8.0/en/server-error-reference.html#error_er_net_packet_too_large) -Fehler (der in der `exception.log`) und schließt die Verbindung. Bei einigen Kunden erhalten Sie möglicherweise auch eine *Verbindung zum MySQL-Server während der Abfrage unterbrochen* Fehler, wenn das Kommunikationspaket zu groß ist.

<u>Zu reproduzierende Schritte</u>

Dieses Problem kann durch eine Vielzahl von Aufgaben auftreten. Dazu kann der Versuch gehören, eine große Anzahl von Produkten in Adobe Commerce zu importieren, oder Transaktionsabfragen, die zu viele Daten zurücksenden. Das Ergebnis sind Datenbankverbindungsfehler in `var/log/exception.log` und anderen Problemen, z. B. nicht erfolgreich importierte Produkte.

## Ursache

Der Standardwert von 16 MB für MySQL `max_allowed_packets` -Einstellung ist nicht groß genug für Ihre Anforderungen.

## Lösung

1. Identifizieren von Abfragen, bei denen die einzelnen Zeilen die aktuelle Zeile überschreiten `max_allowed_packet` Limit. Solche Abfragen müssen umgeschrieben werden, um die Menge der zurückgegebenen Daten zu reduzieren. Dies kann durch eine kleinere Anzahl von Spalten im `SELECT` -Anweisung oder wählen Sie einen kleineren Datentyp für verschiedene Spalten als Teil des Tabellenentwurfs aus. Wenn Sie über ein New Relic-Konto verfügen, verwenden Sie die [New Relic APM-Fehlerseite](https://docs.newrelic.com/docs/apm/apm-ui-pages/error-analytics/errors-page-explore-events-behind-errors) und [New Relic APM-Datenbankseite](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time), und [New Relic-Protokolle](https://docs.newrelic.com/docs/logs/log-management/get-started/get-started-log-management) um nach den relevanten Abfragen zu suchen.
1. Zur schnellen Behebung können Sie die `max_allowed_packet` Größe, die bei der [Einreichen eines Tickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), dies liegt jedoch im Ermessen des Customer Engineering-Teams, da ein zu großer Teil des Werts zu Replikationsfehlern führen kann, da dies zu Netzwerküberlastung führt.
1. Als Best Practice sollten Sie den folgenden Befehl in Ihrer CLI für einige Ihrer großen Datenbanktabellen ausführen:

   ```
   show table status like [table name to match]
   ```

   Bewerten Sie die auf diesen Tabellen ausgeführten Abfragen, um festzustellen, ob Sie die empfohlene `max_allowed_packet` 16 MB. Führen Sie denselben Prozess in Schritt 1 aus, um die von solchen Abfragen zurückgegebenen Daten zu reduzieren.

## Verwandtes Lesen

* [Installationsanleitung > MySQL](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/mysql.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=max%20allowed%2016%20MB) in unserer Entwicklerdokumentation.
* [Beim Hochladen der Datenbank wird die Verbindung zu MySQL unterbrochen](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md) in unserer Wissensdatenbank.
* [Best Practices für Datenbanken mit Adobe Commerce in Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) in unserer Wissensdatenbank.
* [Best Practices zur Lösung von Problemen mit der Datenbankleistung](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) in unserer Wissensdatenbank.
