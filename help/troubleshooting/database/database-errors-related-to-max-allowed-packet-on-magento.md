---
title: Datenbankfehler im Zusammenhang mit „max_allowed_package“ in Adobe Commerce
description: Dieser Artikel bietet eine Lösung für Datenbankverbindungsfehler in "var/log/exception.log", die beim Importieren einer großen Anzahl von Produkten oder bei der Durchführung einer anderen Aufgabe auftreten können, die den Server zwingt, größere Pakete zu verarbeiten als in „max_allowed_package“ festgelegt, die größer als der Standardwert (16 MB) sind.
exl-id: e8932b72-91a3-43ea-800e-a6c7a5a17656
feature: Best Practices, Observability, Services
role: Developer
source-git-commit: 5ca7a4400e62db2419b32a31a4f6cf04f5a82e35
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Datenbankfehler im Zusammenhang mit „max_allowed_package“ in Adobe Commerce

Dieser Artikel bietet eine Lösung für Datenbankverbindungsfehler in der `var/log/exception.log`, die beim Importieren einer großen Anzahl von Produkten oder beim Ausführen einer anderen Aufgabe auftreten können, die den Server zwingt, größere Pakete zu verarbeiten als in `max_allowed_packet` festgelegt, die größer als der Standardwert (16 MB) ist.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premise, alle [unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Wenn ein [!DNL MySQL]-Client oder der [mysqld](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html)-Server ein Paket erhält, das größer als [max\_allowed\_package](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html#sysvar_max_allowed_packet) Byte ist, gibt er einen [ER\_NET\_PACKET\_TOO\_LARGE](https://dev.mysql.com/doc/mysql-errors/8.0/en/server-error-reference.html#error_er_net_packet_too_large)-Fehler aus (der in der `exception.log` zu sehen ist) und schließt die Verbindung. Bei einigen Clients tritt möglicherweise auch ein Fehler *Verbindung zum Server während [!DNL MySQL] Abfrage unterbrochen* auf, wenn das Kommunikationspaket zu groß ist.

<u>Schritte zur Reproduktion</u>

Dieses Problem kann durch eine Vielzahl von Aufgaben verursacht werden. Dazu kann der Versuch gehören, eine große Anzahl von Produkten in Adobe Commerce zu importieren, oder Transaktionsabfragen, die zu viele Daten zurücksenden. Das Ergebnis sind Datenbankverbindungsfehler in `var/log/exception.log` und andere Probleme, wie z. B. nicht erfolgreich importierte Produkte.

## Ursache

Der Standardwert von 16 MB für die Einstellung [!DNL MySQL] `max_allowed_packets` ist nicht groß genug für Ihre Anforderungen.

## Lösung

1. Identifizieren Sie Abfragen, bei denen die einzelnen Zeilen das aktuelle `max_allowed_packet` überschreiten. Solche Abfragen müssen neu geschrieben werden, um die Menge der zurückgegebenen Daten zu reduzieren. Dies kann durch eine kleinere Anzahl von Spalten in der `SELECT`-Anweisung oder durch Auswahl eines kleineren Datentyps für verschiedene Spalten als Teil des Tabellendesigns erfolgen. Wenn Sie über ein New Relic-Konto verfügen, verwenden Sie die Seite [New Relic APM-Fehler](https://docs.newrelic.com/docs/apm/apm-ui-pages/error-analytics/errors-page-explore-events-behind-errors) und die Seite [New Relic APM-Datenbanken](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time) und [New Relic-](https://docs.newrelic.com/docs/logs/log-management/get-started/get-started-log-management), um nach den entsprechenden Abfragen zu suchen.
1. Zur schnellen Behebung können Sie beim `max_allowed_packet` eines Tickets vorübergehend eine Erhöhung der [&#x200B; anfordern](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) Dies liegt jedoch im Ermessen des Customer Engineering-Teams, da eine zu große Menge eines Werts zu Replikationsfehlern führen kann, da dies zu Netzwerkengpässen führt.
1. Als Best Practice sollten Sie den folgenden Befehl in Ihrer CLI für einige Ihrer großen Datenbanktabellen ausführen:

   ```
   show table status like [table name to match]
   ```

   Werten Sie die Abfragen aus, die für diese Tabellen ausgeführt werden, um festzustellen, ob Sie die empfohlene `max_allowed_packet` von 16 MB überschreiten. Führen Sie denselben Prozess in Schritt 1 aus, um die von solchen Abfragen zurückgegebenen Daten zu reduzieren.

## Verwandtes Lesen

* [Übersicht über die lokale Installation](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/overview) in unserer Entwicklerdokumentation.
* [Best Practices für Datenbanken für Adobe Commerce auf Cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)Infrastrukturen in unserer Support-Wissensdatenbank.
* [Best Practices zur Behebung von Problemen mit &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) Datenbankleistung - in unserer Support-Wissensdatenbank.
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
