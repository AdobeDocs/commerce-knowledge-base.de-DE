---
title: '[!DNL MySQL] Speicherplatz auf Adobe Commerce in der Cloud-Infrastruktur ist knapp'
description: Dieser Artikel bietet Lösungen für Fälle, in denen nur sehr wenig oder kein Speicherplatz für  [!DNL MySQL] -on Adobe Commerce in der Cloud-Infrastruktur vorhanden ist. Zu den Symptomen zählen Standortausfälle, Kunden, die keine Produkte in den Warenkorb legen können, keine Verbindung zur Datenbank herstellen können, Remote-Zugriff auf die Datenbank und keine Möglichkeit, SSH in den Knoten einzufügen. Zu den Symptomen gehören auch Galera-, Umgebungs-, PHP-, Datenbank- und Bereitstellungsfehler, wie unten aufgeführt. Klicken Sie auf [Lösung](https://support.magento.com/hc/en-us/articles/360058472572#solution), um direkt zum Abschnitt Lösung zu springen.
exl-id: 788c709e-59f5-4062-ab25-5ce6508f29f9
feature: Catalog Management, Categories, Cloud, Paas, Services
role: Developer
source-git-commit: 80343c834563e7550569d225979edfa6a997bcfc
workflow-type: tm+mt
source-wordcount: '1319'
ht-degree: 0%

---

# [!DNL MySQL] Speicherplatz auf Adobe Commerce in der Cloud-Infrastruktur ist knapp

Dieser Artikel bietet Lösungen für Fälle, in denen nur sehr wenig oder kein Speicherplatz für [!DNL MySQL] auf Adobe Commerce in der Cloud-Infrastruktur vorhanden ist. Zu den Symptomen gehören Standortausfälle, Kunden, die keine Produkte in den Warenkorb legen können, die keine Verbindung zur Datenbank herstellen können, der Remote-Zugriff auf die Datenbank und die Unfähigkeit, SSH in den Knoten einzufügen. Zu den Symptomen gehören auch Galera-, Umgebungs-, PHP-, Datenbank- und Bereitstellungsfehler, wie unten aufgeführt. Klicken Sie auf [Lösung](https://support.magento.com/hc/en-us/articles/360058472572#solution), um direkt zum Abschnitt „Lösung“ zu springen.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur 2.3.0-2.3.6-p1, 2.4.0-2.4.2

## Problem

Die Datenbank wird zu groß. Zu den Symptomen zählen u. a. der Verlust der Datenbankverbindung, ein Fehler beim Hochladen der Datenbank und eine Vielzahl anderer Probleme.

Fehler, auf die Sie stoßen können:

Galera:

* *SQLSTATE\[08S01\]: Kommunikationsverbindungsfehler: 1047 WSREP hat den Knoten noch nicht für die Verwendung durch die Anwendung vorbereitet*   *Importfehler:*
* *SQLSTATE\[HY000\]: Allgemeiner Fehler: 1180 Fehler 5 „Eingabe/Ausgabe-Fehler“*
* *SQLSTATE\[08S01\]: Kommunikationsverbindungsfehler: 1047 WSREP hat den Knoten noch nicht für die Verwendung durch die Anwendung vorbereitet*

Fehler bei der Umgebungssynchronisierung:

* *SQLSTATE: Allgemeiner Fehler: 1180 hat Fehler 5 „Eingabe/Ausgabe-Fehler“ während des COMMIT erhalten*

PHP-Fehler:

* *php: PDO::\_\_struct(): [!DNL MySQL] Server ist verschwunden.*
* *php-Fehler: PDO::\_\_struct(): Fehler beim Lesen des Grußpakets. PID=NNN.*
* *ERROR 2013 (HY000): Verbindung zu [!DNL MySQL] Server beim &#39;Lesen des ersten Kommunikationspakets&#39; unterbrochen, Systemfehler: 0 „Interner Fehler/Überprüfung (Nicht Systemfehler)“.*

Datenbankfehler:

* *ERROR\_CODE: 1114*
* *InnoDB: Fehler (Nicht genügend Speicherplatz) beim Schreiben des Word-Knotens in die FTS-Hilfs-Indextabelle.*
* *SQLSTATE\[HY000\]: Allgemeiner Fehler: 2006 [!DNL MySQL] Server wurde entfernt*
* *\[ERROR\] Slave SQL: Fehler &#39;Die `<table\_name>` ist voll&#39; bei der Abfrage.*
* *Unit mysql.service ist in den Fehlerstatus übergegangen.*
* *Fehler: &#39;Verbindung zum lokalen [!DNL MySQL]-Server über Socket &#39;/var/run/mysqld/mysqld.sock&#39; nicht möglich (111 „Verbindung verweigert„)&#39;*
* *1205 Sperrwartezeitlimit überschritten. Versuchen Sie, die Transaktion neu zu starten. Abfrage war: INSERT INTO \`cron\_schedule\` (\`job\_code\`, \`status\`, \`created\_at\`, \`scheduled\_at\`) VALUES (?, ?, `YYYY-02-07 HH:MM:SS`, `YYYY-MM-DD HH:MM:SS`)*

Bereitstellungsfehler:

* *E: Befehl &#39;\[&#39;sudo&#39;, &#39;-u&#39;, `<environment name>`, &#39;bash&#39;, &#39;-c&#39;, &#39;/etc/platform/`<environment name>`/post\_deploy.sh&#39;\]&#39; hat den Exitstatus 255 zurückgegeben, der nicht null ist*
* *E: Befehl &#39;\[&#39;ssh&#39;, u`<node IP address>`, &#39;sudo /usr/bin/sv -w 30 restart site-`<environment name>`g-nginx&#39;\]&#39; ergab einen Wert ungleich null*
* *Schema wird aktualisiert.. SQLSTATE\[HY000\]: Allgemeiner Fehler: 1114 Die Tabelle `<table\_name>` ist voll*
* *SQLSTATE\[HY000\]: Allgemeiner Fehler: 3 Fehler beim Schreiben der Datei ./`<environment name>`/\#*
* *W: `<filename>` (Errcode: 28 „No space left on device„)* *Indizierungsfehler (zusammen mit verwaisten temporären .ibd-Dateien in /tmp):*
* *Katalogregel-Indexer löst eine Ausnahme aus. Die temporären Tabellen werden im Anschluss nicht bereinigt und füllen dann die Festplatte auf dem aktuellen [!DNL MySQL] Master-Knoten*

<u>Schritte zur Reproduktion</u>:

Sie können unter anderem überprüfen, ob die `/data/mysql` (oder wo auch immer [!DNL MySQL] Datenspeicher konfiguriert ist) voll ist, indem Sie den folgenden Befehl in der CLI ausführen:

```bash
df -h
```

Weniger als 10 % des freien Speichers auf [!DNL MySQL] Festplatte ist ein primärer Indikator für einen Ausfall.

## Ursache

Die `/data/mysql`-Bereitstellung könnte aufgrund einer Reihe von Problemen ausgelastet sein, z. B. weil nicht genügend Inodes, verfügbarer Speicherplatz und fehlerhafte Abfragen vorhanden sind, die temporäre Tabellen generieren.

## Lösung

Es gibt einen sofortigen Schritt, den Sie unternehmen können, um [!DNL MySQL] wieder auf den richtigen Weg zu bringen (oder zu verhindern, dass es stecken bleibt): Machen Sie Platz frei, indem Sie große Tische spülen.

Eine langfristige Lösung bestünde jedoch darin, mehr Speicherplatz zuzuweisen und den Best Practices für [Datenbank](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) zu folgen, einschließlich der Aktivierung der Funktion [Bestellung/Rechnung/Versand](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-archive).

Im Folgenden finden Sie Details zu schnellen und langfristigen Lösungen.

### Überprüfen und Freigeben von Knoten

Stellen Sie sicher, dass ausreichend Knoten verfügbar sind. Führen Sie dazu den folgenden Befehl aus:

```bash
df -i
```

Die Ausgabe würde in etwa wie folgt aussehen:

```bash
Filesystem Inodes   Used   Free Use% Mounted on
/dev/nvme2n1 655360    1695  653665    1% /data/mysql
```

Überprüfen, ob % Verwendung &lt; 70 % ist. Inodes sind mit Dateien korreliert. Wenn Sie Dateien aus der Partition entfernen, werden Inodes freigegeben.

### Überprüfen und Freigeben von Speicherplatz

Überprüfen Sie den verfügbaren Speicherplatz. Führen Sie dazu Folgendes aus:

```bash
df -k
```

Die Ausgabe würde in etwa wie folgt aussehen:

```bash
Size Used Avail Use% Mounted on·
       50G 49G 95M 100% /data/mysql
```

Wenn der Wert % > 70 % ist, müssen Sie Maßnahmen ergreifen, um Speicherplatz freizugeben bzw. hinzuzufügen.

### Auf große `ibtmp1` prüfen

Auf große `ibtmp1`-Dateien `/data/mysql` jedem Knoten prüfen: Diese Datei ist der Tablespace für temporäre Tabellen. Wenn es ungültige Abfragen gibt, die temporäre Tabellen generieren, sind diese in der `ibtmp1` enthalten. Diese Datei wird nur entfernt, wenn die Datenbank neu gestartet wird. Wenn sie den gesamten verfügbaren Speicherplatz belegt, muss die Datenbank neu gestartet werden. Wenn ungültige Abfragen vorhanden sind, wird sie erneut erstellt.

### Große Tabellen spülen

>[!WARNING]
>
>Es wird dringend empfohlen, ein Datenbank-Backup zu erstellen, bevor Sie Änderungen durchführen und diese in Zeiten hoher Site-Auslastung vermeiden. Siehe [Dump Ihrer Datenbank](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots) in unserer Entwicklerdokumentation.

Überprüfen Sie, ob große Tabellen vorhanden sind, und prüfen Sie, ob eine davon geleert werden kann. Gehen Sie dazu auf dem primären Knoten (Quellknoten) vor.

Beispielsweise können Tabellen mit Berichten normalerweise geleert werden. Weitere Informationen zum Suchen großer Tabellen finden Sie im Artikel [Suchen  [!DNL MySQL]  großen Tabellen](/help/how-to/general/find-large-mysql-tables.md).

Wenn keine großen Berichtstabellen vorhanden sind, sollten Sie `_index` Tabellen leeren, um die Adobe Commerce-Anwendung wieder auf den richtigen Weg zu bringen. `index_price` Tabellen wären die besten Kandidaten. Beispiel: `catalog_category_product_index_storeX` Tabellen, bei denen X Werte von „1“ bis zur maximalen Speicheranzahl aufweisen kann. Beachten Sie, dass Sie eine Neuindizierung durchführen müssen, um die Daten in diesen Tabellen wiederherzustellen. Bei großen Katalogen kann diese Neuindizierung sehr lange dauern.

Warten Sie nach dem Leeren auf den Abschluss der WSREP-Synchronisierung. Sie können jetzt Sicherungskopien erstellen und wichtigere Schritte ausführen, um mehr Speicherplatz hinzuzufügen, z. B. mehr Speicherplatz zuweisen/kaufen und die Funktion [Bestellung/Rechnung/](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-archive) aktivieren.

### Überprüfen der binären Protokollierungseinstellungen

Überprüfen Sie die Binärprotokollierungseinstellungen Ihres [!DNL MySQL]-Servers: `log_bin` und `log_bin_index`. Wenn die Einstellungen aktiviert sind, können die Protokolldateien sehr groß werden. [Erstellen Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) mit der Aufforderung, große Binärlogdateien zu bereinigen. Vergewissern Sie sich außerdem, dass die Binärprotokollierung korrekt konfiguriert ist, sodass Protokolle regelmäßig bereinigt werden und nicht zu viel Speicherplatz beanspruchen.

Wenn Sie keinen Zugriff auf [!DNL MySQL] Server-Einstellungen haben, bitten Sie den Support um Überprüfung.

### Freigeben von ungenutztem zugewiesenem Speicherplatz

1. SSH in Knoten 1 einloggen und sich bei MySQL anmelden:

   ```sh
   mysql -h127.0.0.1 -p`php -r "echo (include('app/etc/env.php'))['db']['connection']['default']['password'];"` -u`whoami` `whoami`
   ```

   Ausführliche Anweisungen finden Sie unter [Verbinden und Ausführen von Abfragen für die Adobe Commerce-Datenbank](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/backend-development/remote-db-connection-execute-queries).

1. Auf nicht verwendeten Speicherplatz prüfen:

   ```sql
   SELECT table_name, round((data_length+index_length)/1048576,2) AS size_MB, round((data_free)/1048576,2) AS Allocated_but_unused FROM information_schema.tables WHERE data_free > 1048576*10 ORDER BY data_free DESC;
   ```


   Beispielausgabe:

   | table_name | size_MB | Allocate_but_unused |
   |----------------------|----------|--------------------------|
   | vertex_taxrequest | 28145,20 | 14943,00 |


   Überprüfen Sie die Ausgabe, um festzustellen, ob Speicher vorhanden ist, der zugewiesen wurde, aber nicht verwendet wird. Dies tritt auf, wenn Daten aus einer Tabelle gelöscht wurden, der Speicher dieser Tabelle jedoch noch zugewiesen ist.


1. Setzen Sie Ihre Site in den Wartungsmodus und stoppen Sie Cron-Aufträge, damit keine Interaktionen in der Datenbank stattfinden. Anweisungen hierzu finden Sie unter [Wartungsmodus aktivieren oder deaktivieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) und [Cron-Aufträge deaktivieren](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property#disable-cron-jobs).
1. Geben Sie diesen Platz zurück, indem Sie die Tabelle mit dem folgenden Befehl neu erstellen (beispielsweise unter Verwendung der oben aufgeführten Tabelle mit dem am meisten ungenutzten Platz):

   ```sql
   ALTER TABLE vertex_taxrequest Engine = "INNODB";
   ```

1. Führen Sie die folgende Abfrage aus, um nach nicht zugewiesenem Speicherplatz für jede Tabelle zu suchen, die einen hohen Wert im **[!UICONTROL Allocated_but_unused]** anzeigt.

   ```sql
   SELECT table_name, round((data_length+index_length)/1048576,2) as size_MB, round((data_free)/1048576,2) as Allocated_but_unused FROM information_schema.tables WHERE 1 AND data_free > 1048576*10 ORDER BY 
   data_free DESC;
   ```


1. Jetzt [Wartungsmodus deaktivieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#enable-or-disable-maintenance-mode-1) und [Cron-Aufträge aktivieren](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property#disable-cron-jobs).


### Mehr Speicherplatz zuweisen/kaufen

Weisen Sie mehr Speicherplatz für [!DNL MySQL] zu, wenn Sie nicht verwendeten Speicherplatz haben. Informationen [ Überprüfen, ob Sie über freien Speicherplatz verfügen](/help/how-to/general/check-disk-space-limit-for-magento-commerce-cloud.md) finden Sie im Artikel „Überprüfen des Speicherplatzlimits“.

* Für den Starter-Plan, alle Umgebungen und Pro-Plan-Integrationsumgebungen können Sie den Speicherplatz zuweisen, wenn Sie einige ungenutzte haben. Weitere Informationen finden Sie unter [Mehr Platz zuweisen für [!DNL MySQL]](/help/how-to/general/allocate-more-space-for-mysql-in-magento-commerce-cloud.md).
* Bei Pro Plan Staging- und Produktionsumgebungen [wenden Sie sich an den ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um bei ungenutzten Festplatten mehr Speicherplatz zuzuweisen.

Wenn Sie Ihr Speicherplatzlimit erreicht haben und weiterhin Probleme mit wenig Speicherplatz haben, sollten Sie ggf. weiteren Speicherplatz kaufen. Weitere Informationen erhalten Sie von Ihrem Adobe-Account-Team.

## Verwandtes Lesen

[Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
