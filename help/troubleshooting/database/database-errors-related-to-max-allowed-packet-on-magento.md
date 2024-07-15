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

Dieser Artikel bietet eine Lösung für Fehler bei der Datenbankverbindung in der `var/log/exception.log`, die beim Import einer großen Anzahl von Produkten oder bei der Ausführung einer anderen Aufgabe auftreten können, die den Server zwingt, größere Pakete als in `max_allowed_packet` festgelegt zu verarbeiten, die größer als die Standardgröße von 16 MB sind.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort, alle [unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Wenn ein MySQL-Client oder der Server [mysqld](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html) ein Paket empfängt, das größer ist als [max\_allowed\_packet](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html#sysvar_max_allowed_packet), wird ein [ER\_NET\_PACKET\_TOO\_LARGE](https://dev.mysql.com/doc/mysql-errors/8.0/en/server-error-reference.html#error_er_net_packet_too_large) -Fehler ausgegeben (der in `exception.log` sichtbar ist) und die Verbindung geschlossen. Bei einigen Clients erhalten Sie möglicherweise auch einen Fehler vom Typ *Verlorene Verbindung zum MySQL-Server während der Abfrage*, wenn das Kommunikationspaket zu groß ist.

<u>Zu reproduzierende Schritte</u>

Dieses Problem kann durch eine Vielzahl von Aufgaben auftreten. Dazu kann der Versuch gehören, eine große Anzahl von Produkten in Adobe Commerce zu importieren, oder Transaktionsabfragen, die zu viele Daten zurücksenden. Das Ergebnis sind Fehler bei der Datenbankverbindung in `var/log/exception.log` und andere Probleme, z. B. wenn Produkte nicht erfolgreich importiert wurden.

## Ursache

Der Standardwert von 16 MB für die Einstellung MySQL `max_allowed_packets` ist nicht groß genug für Ihre Anforderungen.

## Lösung

1. Identifizieren Sie Abfragen, bei denen die einzelnen Zeilen die aktuelle `max_allowed_packet` -Grenze überschreiten. Solche Abfragen müssen umgeschrieben werden, um die Menge der zurückgegebenen Daten zu reduzieren. Dies kann durch eine kleinere Anzahl von Spalten in der `SELECT` -Anweisung oder die Auswahl eines kleineren Datentyps für verschiedene Spalten als Teil des Tabellenentwurfs erfolgen. Wenn Sie über ein New Relic-Konto verfügen, verwenden Sie die Seite [New Relic APM-Fehler](https://docs.newrelic.com/docs/apm/apm-ui-pages/error-analytics/errors-page-explore-events-behind-errors) und die Seite [New Relic APM-Datenbanken](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time) und [New Relic-Protokolle](https://docs.newrelic.com/docs/logs/log-management/get-started/get-started-log-management) , um nach den entsprechenden Abfragen zu suchen.
1. Zur schnellen Behebung können Sie vorübergehend eine Erhöhung der `max_allowed_packet`-Größe anfordern, wenn Sie [ein Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Dies liegt jedoch im Ermessen des Customer Engineering-Teams, da zu viel Wert zu Replikationsfehler verursachen kann, da dies zu einer Netzwerküberlastung führt.
1. Als Best Practice sollten Sie den folgenden Befehl in Ihrer CLI für einige Ihrer großen Datenbanktabellen ausführen:

   ```
   show table status like [table name to match]
   ```

   Bewerten Sie die auf diesen Tabellen ausgeführten Abfragen, um festzustellen, ob Sie die empfohlene `max_allowed_packet` -Größe von 16 MB überschreiten. Führen Sie denselben Prozess in Schritt 1 aus, um die von solchen Abfragen zurückgegebenen Daten zu reduzieren.

## Verwandtes Lesen

* [Installationsanleitung > MySQL](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/mysql.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=max%20allowed%2016%20MB) in unserer Entwicklerdokumentation.
* [Der Upload der Datenbank verliert die Verbindung zu MySQL](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md) in unserer Support-Wissensdatenbank.
* [Best Practices für die Datenbank für Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) in unserer Support-Wissensdatenbank.
* [Best Practices zur Lösung von Problemen mit der Datenbankleistung](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) in unserer Support-Wissensdatenbank.
