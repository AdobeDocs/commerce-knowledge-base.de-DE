---
title: MySQL-Speicherplatz in Adobe Commerce in der Cloud-Infrastruktur ist gering
description: Dieser Artikel bietet Lösungen für Fälle, in denen MySQL in Adobe Commerce nur über sehr wenig Platz oder keinen Speicherplatz für die Cloud-Infrastruktur zur Verfügung steht. Zu den Symptomen zählen Site-Ausfälle, Kunden, die nicht in der Lage sind, Produkte zum Warenkorb hinzuzufügen, nicht in der Lage, eine Verbindung zur Datenbank herzustellen, remote auf die Datenbank zuzugreifen und SSH nicht in den Knoten integrieren zu können. Zu den Symptomen gehören auch Galera-, Umgebungs-, PHP-, Datenbank- und Bereitstellungsfehler, wie unten aufgeführt. Klicken Sie auf [Lösung](https://support.magento.com/hc/en-us/articles/360058472572#solution), um direkt zum Lösungsabschnitt zu springen.
exl-id: 788c709e-59f5-4062-ab25-5ce6508f29f9
feature: Catalog Management, Categories, Cloud, Paas, Services
role: Developer
source-git-commit: 667fcacd5b6cbf56a5fd919d0683ad6a0f979fca
workflow-type: tm+mt
source-wordcount: '1157'
ht-degree: 0%

---

# MySQL-Speicherplatz in Adobe Commerce in der Cloud-Infrastruktur ist gering

Dieser Artikel bietet Lösungen für Fälle, in denen MySQL in Adobe Commerce nur über sehr wenig Platz oder keinen Speicherplatz für die Cloud-Infrastruktur zur Verfügung steht. Zu den Symptomen zählen Site-Ausfälle, Kunden, die nicht in der Lage sind, Produkte zum Warenkorb hinzuzufügen, nicht in der Lage, eine Verbindung zur Datenbank herzustellen, remote auf die Datenbank zuzugreifen und SSH nicht in den Knoten integrieren zu können. Zu den Symptomen gehören auch Galera-, Umgebungs-, PHP-, Datenbank- und Bereitstellungsfehler, wie unten aufgeführt. Klicken Sie auf [Lösung](https://support.magento.com/hc/en-us/articles/360058472572#solution) , um direkt zum Lösungsabschnitt zu springen.

## Betroffene Produkte und Versionen

Adobe Commerce für Cloud-Infrastruktur 2.3.0-2.3.6-p1, 2.4.0-2.4.2

## Problem

Die Datenbank wird zu groß. Zu den Symptomen zählen der Verlust der Datenbankverbindung, ein Fehler beim Hochladen der Datenbank und eine Vielzahl anderer Probleme.

Eventuelle Fehler:

Galera:

* *SQLSTATE\[08S01\]: Kommunikationslink-Fehler: 1047 WSREP hat den Knoten noch nicht für die Anwendungsnutzung vorbereitet*   *Importfehler:*
* *SQLSTATE\[HY000\]: Allgemeiner Fehler: 1180 Fehler 5 &quot;Input/output error&quot;*
* *SQLSTATE\[08S01\]: Kommunikationslink-Fehler: 1047 WSREP hat den Knoten noch nicht für die Anwendungsnutzung vorbereitet*

Fehler bei der Umgebungssynchronisierung:

* *SQLSTATE: Allgemeiner Fehler: 1180 Got error 5 &quot;Input/output error&quot; during COMMIT*

PHP-Fehler:

* *php: PDO:\_\_konstrukt(): Der MySQL-Server ist verschwunden.*
* *php errors: PDO::\_\_struct(): Fehler beim Lesen des Grußpakets. PID=NNN.*
* *ERROR 2013 (HY000): Verlorene Verbindung zum MySQL-Server beim Lesen des anfänglichen Kommunikationspakets, Systemfehler: 0 &quot;Interner Fehler/Prüfung (kein Systemfehler)&quot;.*

Datenbankfehler:

* *Fehler\_code: 1114*
* *InnoDB: Fehler (Nicht genügend Speicherplatz) beim Schreiben des Wortknotens in die FTS-Hilfsindextabelle.*
* *SQLSTATE\[HY000\]: Allgemeiner Fehler: MySQL-Server 2006 wurde entfernt*
* *\[FEHLER\] Slave SQL: Fehler &#39;Die Tabelle `<table\_name>` ist voll&#39; bei der Abfrage.*
* *Unit mysql.service ist in den Fehlerstatus versetzt.*
* *error: &#39;Kann über Socket &#39;/var/run/mysqld/mysqld.sock&#39; keine Verbindung zum lokalen MySQL-Server herstellen (111 &quot;Verbindung verweigert&quot;)&#39;*
* *1205 Zeitüberschreitung bei Sperrung überschritten; Versuch, die Transaktion neu zu starten, Abfrage lautete: IN \`cron\_schedule\` (\`job\_code\`, \`status\`, \`created\_at\`, \`scheduled\_at\`) WERTE (?, ?, `YYYY-02-07 HH:MM:SS`, `YYYY-MM-DD HH:MM:SS`)*

Bereitstellungsfehler:

* *E: Befehl &#39;\[&#39;sudo&#39;, &#39;-u&#39;, `<environment name>`, &#39;bash&#39;, &#39;-c&#39;, &#39;/etc/platform/`<environment name>`/post\_deploy.sh&#39;\]&#39; gibt den Ausstiegsstatus &quot;Nicht null&quot;zurück. 255*
* *E: Befehl &#39;\[&#39;ssh&#39;, u`<node IP address>`, &#39;sudo /usr/bin/sv -w 30 Neustart Site-`<environment name>`g-nginx&#39;\]&#39; gibt nicht null* zurück
* *Schema aktualisieren.. SQLSTATE\[HY000\]: Allgemeiner Fehler: 1114 Die Tabelle `<table\_name>` ist voll*
* *SQLSTATE\[HY000\]: Allgemeiner Fehler: 3 Fehler beim Schreiben der Datei ./`<environment name>`/\#*
* *W: `<filename>` (Fehler: 28 &quot;Kein Speicherplatz auf Gerät mehr&quot;)* *Indizierungsfehler (zusammen mit verwaisten temporären .ibd-Dateien in /tmp):*
* *Der Indexer für Katalogregeln gibt eine Ausnahme aus. Die temporären Tabellen werden im Nachhinein nicht bereinigt und füllen dann den Datenträger auf dem aktuellen MySQL-Master-Knoten* aus

<u>Zu reproduzierende Schritte</u>:

Sie können überprüfen, ob der `/data/mysql` (oder wo auch immer die MySQL-Datenspeicherung konfiguriert ist) voll ist, indem Sie den folgenden Befehl in der CLI ausführen:

```bash
df -h
```

Weniger als 10 % des freien Speichers auf der MySQL-Festplatte ist ein primärer Indikator für einen Ausfall.

## Ursache

Das `/data/mysql` -Reittier kann aufgrund einer Reihe von Problemen voll sein, z. B. aufgrund des Fehlens von genügend Inoden, verfügbarem Speicherplatz und schlechter Abfragen, die temporäre Tabellen generieren.

## Lösung

Es gibt einen sofortigen Schritt, den Sie unternehmen könnten, um MySQL wieder auf den richtigen Weg zu bringen (oder zu verhindern, dass es blockiert wird): Freiräumen Sie, indem Sie große Tabellen leeren.

Eine langfristige Lösung würde jedoch mehr Speicherplatz zuweisen und den [Best Practices für die Datenbank](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) folgen, einschließlich der Aktivierung der [Archiv für Bestellung/Rechnung/Sendung](https://docs.magento.com/user-guide/sales/order-archive.html) -Funktionalität.

Im Folgenden finden Sie Details zu schnellen und langfristigen Lösungen.

### Checken und Freigeben von Anschlüssen

Stellen Sie sicher, dass genügend verfügbare Nodes vorhanden sind. Führen Sie dazu den folgenden Befehl aus:

```bash
df -i
```

Die Ausgabe würde in etwa wie folgt aussehen:

```bash
Filesystem Inodes   Used   Free Use% Mounted on
/dev/nvme2n1 655360    1695  653665    1% /data/mysql
```

Stellen Sie sicher, dass &quot;Use %&quot;&lt; 70 % ist. Knoten werden mit Dateien korreliert. Wenn Sie Dateien aus der Partition entfernen, werden Sie Inodes freigeben.

### Speicherplatz einchecken und freigeben

Überprüfen Sie den verfügbaren Speicherplatz. Führen Sie dazu Folgendes aus:

```bash
df -k
```

Die Ausgabe würde der folgenden ähneln:

```bash
Size Used Avail Use% Mounted on·
       50G 49G 95M 100% /data/mysql
```

Wenn die Option % verwenden > 70 % beträgt, müssen Sie Maßnahmen ergreifen, um Speicherplatz freizugeben/hinzuzufügen.

### Überprüfen auf große `ibtmp1` -Dateien

Überprüfen Sie auf eine große `ibtmp1` -Datei auf `/data/mysql` jedes Knotens: Diese Datei ist der Tablespace für temporäre Tabellen. Bei fehlerhaften Abfragen, die temporäre Tabellen generieren, sind diese in der Datei &quot;`ibtmp1`&quot;enthalten. Diese Datei wird nur entfernt, wenn die Datenbank neu gestartet wird. Wenn der gesamte verfügbare Speicherplatz belegt wird, muss die Datenbank neu gestartet werden. Bei fehlerhaften Abfragen wird sie erneut erstellt.

### Große Tabellen leeren

>[!WARNING]
>
>Es wird dringend empfohlen, eine Datenbanksicherung zu erstellen, bevor Sie Manipulationen durchführen und sie bei hohen Site-Ladezeiten vermeiden. Siehe [Dump your database](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump) in unserer Entwicklerdokumentation.

Überprüfen Sie, ob große Tabellen vorhanden sind, und überlegen Sie, ob eine davon geleert werden kann. Führen Sie dies auf dem primären (Quell-)Knoten durch.

Beispielsweise können Tabellen mit Berichten in der Regel geleert werden. Weitere Informationen zum Suchen großer Tabellen finden Sie im Artikel [Große MySQL-Tabellen suchen](/help/how-to/general/find-large-mysql-tables.md) .

Wenn keine riesigen Berichtstabellen vorhanden sind, sollten Sie erwägen, `_index` -Tabellen zu leeren, um die Adobe Commerce-Anwendung wieder auf die richtige Weise zu übermitteln. `index_price` Tabellen wären die besten Kandidaten. Beispiel: `catalog_category_product_index_storeX` -Tabellen, wobei X Werte von &quot;1&quot;bis zur maximalen Speicheranzahl aufweisen kann. Beachten Sie bitte, dass Sie eine Neuindizierung durchführen müssen, um Daten in diesen Tabellen wiederherzustellen. Im Falle großer Kataloge kann diese Neuindizierung viel Zeit in Anspruch nehmen.

Nachdem Sie sie geleert haben, warten Sie auf den Abschluss der Browsersynchronisierung. Sie können jetzt Backups erstellen und bedeutendere Schritte ausführen, um mehr Platz hinzuzufügen, z. B. mehr Speicherplatz zuzuweisen/zu erwerben und die Funktionalität des Archivs [Bestellung/Rechnungsstellung/Versand](https://docs.magento.com/user-guide/sales/order-archive.html) zu aktivieren.

### Überprüfen der binären Protokollierungseinstellungen

Überprüfen Sie die binären Protokollierungseinstellungen des MySQL-Servers: `log_bin` und `log_bin_index`. Wenn die Einstellungen aktiviert sind, werden die Protokolldateien möglicherweise riesig. [Erstellen Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) mit der Anforderung, große binäre Protokolldateien zu bereinigen. Stellen Sie außerdem sicher, dass die binäre Protokollierung korrekt konfiguriert ist, damit Protokolle regelmäßig bereinigt werden und nicht zu viel Platz benötigt wird.

Wenn Sie keinen Zugriff auf die Einstellungen des MySQL-Servers haben, bitten Sie um Unterstützung, diese zu überprüfen.

### Mehr Speicherplatz zuweisen/kaufen

Weisen Sie MySQL mehr Speicherplatz zu, wenn Sie noch nicht gebraucht haben. Weitere Informationen dazu, wie Sie überprüfen können, ob Sie freien Speicherplatz haben, finden Sie im Artikel [Überprüfen des Festplattenspeicherplatzlimits](/help/how-to/general/check-disk-space-limit-for-magento-commerce-cloud.md) .

* Für den Starter-Plan, alle Umgebungen und die Pro-Plan-Integrationsumgebungen können Sie den Festplattenspeicher zuweisen, wenn Sie nicht mehr verwendet werden. Weitere Informationen finden Sie unter [Mehr Speicherplatz für MySQL zuweisen](/help/how-to/general/allocate-more-space-for-mysql-in-magento-commerce-cloud.md).
* Wenden Sie sich bei Staging- und Produktionsumgebungen für Pro-Plan an den [Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) , um mehr Speicherplatz zuzuweisen, wenn Sie noch nicht genügend Speicherplatz haben.

Wenn Sie Ihre Speicherplatzbeschränkung erreicht haben und dennoch Probleme mit wenig Speicherplatz auftreten, sollten Sie sich für weitere Informationen an Ihr Adobe Account Team wenden.
