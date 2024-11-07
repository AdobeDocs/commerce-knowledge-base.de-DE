---
title: Überprüfen langsamer Abfragen und Prozesse MySQL
description: In diesem Artikel werden einige häufige MySQL-Probleme (langsame Abfragen, zu lange Prozesse) vorgestellt, die sich negativ auf die Site eines Händlers und die von ihm angegebenen Lösungen auswirken können.
exl-id: cae02e4f-d8cb-4074-abac-24ead22bdc07
feature: Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Überprüfen langsamer Abfragen und Prozesse MySQL

In diesem Artikel werden einige häufige MySQL-Probleme (langsame Abfragen, zu lange Prozesse) vorgestellt, die sich negativ auf die Site eines Händlers und die von ihm angegebenen Lösungen auswirken können.

## Überprüfen von MySQL &quot;langsame Abfragen&quot;

### Beschreibung

Wenn Sie einen Ausfall hatten, der möglicherweise durch eine überlastete Datenbank verursacht wurde, helfen Ihnen diese Schritte beim Überprüfen des langsamen Abfrageprotokolls Ihrer Datenbank.

### Abfragen mithilfe der MySQL-Befehlszeile analysieren (Adobe Commerce Cloud/On-Premise/Magento Open Source)

1. Melden Sie sich über die Befehlszeile (Adobe Commerce in der Cloud-Infrastruktur) bei Ihrer MySQL-Befehlszeile (Adobe Commerce On-Premise/Magento Open Source) oder auf Ihrem Cloud-Server an.
1. Prüfen Sie das langsame Abfrageprotokoll auf Abfragen, die länger als 50 Sekunden dauern:

   ```bash
   grep 'Query_time: [5-9][0-9]\|Query_time: [0-9][0-9][0-9]' /var/log/mysql/mysql-slow.log -A 3
   ```

1. Gehen Sie zu <https://www.unixtimestamp.com/> (oder einem ähnlichen Unix-Zeitstempelkonverter) und fügen Sie den Zeitstempel von ein, von dem aus die langsame Abfrage ausgeführt wurde.
1. Wenn die Zeit mit einem Site-Ausfall korreliert, der bei Ihnen aufgetreten ist, kann dies durch eine überlastete Datenbank verursacht werden. Überprüfen Sie, ob die zu diesem Zeitpunkt in der Datenbank geladenen Daten angezeigt wurden. Beispiele für solche Lasten sind:

* Cron-Prozesse
* Traffic (Bots oder Personen)
* Skripte importieren/exportieren
* Erstellen von Dumps


### Analysieren von Abfragen mit [!DNL Percona Toolkit] (nur Adobe Commerce Pro: Cloud-Architektur)

Wenn Ihr Adobe Commerce-Projekt in der Pro-Architektur bereitgestellt wird, können Sie die [!DNL Percona Toolkit] verwenden, um Abfragen zu analysieren.

1. Führen Sie den Befehl `pt-query-digest --type=slowlog` für langsame MySQL-Abfrageprotokolle aus.
   * Informationen zum Speicherort der langsamen Abfrageprotokolle finden Sie unter **[[!UICONTROL Log locations > Service Logs]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)** in unserer Entwicklerdokumentation.
   * Weitere Informationen finden Sie in der Dokumentation zu [[!DNL Percona Toolkit] > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) .
1. Führen Sie je nach den gefundenen Problemen Schritte aus, um die Abfrage zu korrigieren, damit sie schneller ausgeführt wird.

## MySQL &quot;Prozessliste&quot;überprüfen

### Beschreibung

Dadurch lässt sich feststellen, ob der MySQL-Server aktiv ist und keine blockierten Abfragen vorliegen.

### Schritte

1. Melden Sie sich über die Befehlszeile (Adobe Commerce in der Cloud-Infrastruktur) bei Ihrer MySQL-Befehlszeile (Adobe Commerce On-Premise/Magento Open Source) oder auf Ihrem Cloud-Server an.
1. Melden Sie sich mit dem unten stehenden Codeblock bei MySQL an. Dadurch wird der Anmeldevorgang automatisiert.

   ```MySQL
   `export DB_NAME=$(grep [\']db[\'] -A 20 app/etc/env.php | grep dbname | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_HOST=$(grep [\']db[\'] -A 20 app/etc/env.php | grep host | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export DB_USER=$(grep [\']db[\'] -A 20 app/etc/env.php | grep username | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_PWD=$(grep [\']db[\'] -A 20 app/etc/env.php | grep password | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/[']$//" | sed "s/['][,]//");    mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;`
   ```

1. Wenn Sie einen Fehler erhalten oder die Antwort länger als 30 Sekunden dauert, sollten Sie sich an den Support wenden, um den MySQL-Server zu überprüfen.
1. Betrachten Sie die Beispielausgabe.

1. Hier finden Sie eine Beispielausgabe:

   ```MySQL
   `$ mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;'    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | Id        | User          | Host               | db            | Command | Time | State          | Info                                                                                                 | Progress |    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | 123456789 | abcdefghijklm | 192.168.7.10:12345 | abcdefghijklm | Query   |    0 | Writing to net | SELECT `magento_versionscms_hierarchy_node`.*, `page_table`.`title` AS `page_title`, `page_table`.`i |    0.000 |    | 123456788 | abcdefghijklm | 192.168.7.10:12344 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456777 | abcdefghijklm | 192.168.7.10:12333 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456666 | abcdefghijklm | 192.168.5.8:12222  | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |`
   ```

1. Überprüfen Sie die Spalte &quot;Zeit&quot;auf einen Zeitraum, der größer als 1800 Sekunden ist. Dies bedeutet, dass ein Prozess möglicherweise zu viel Zeit in Anspruch nimmt. Notieren Sie den Status der Prozesse in der Spalte &quot;Status&quot;.
1. Überprüfen Sie die Abfragen und töten Sie sie möglicherweise, wenn festgestellt wird, dass sie für diese Dauer nicht ausgeführt werden. Es ist möglich, dass die langwierigen Abfragen erwartet werden.


## Verwandtes Lesen

* [MySQL-Syntax der Verarbeitungsliste anzeigen](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) in dev.mysql.com.
* [MySQL Kill Syntax](https://dev.mysql.com/doc/refman/8.0/en/kill.html) in dev.mysql.com.
* [Sicherheit, Leistung und Datenverarbeitung](https://developer.adobe.com/commerce/php/best-practices/extensions/security/) in unserer Entwicklerdokumentation.
* [MySQL-Hilfe](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql) in unserer Entwicklerdokumentation.
