---
title: Fehlerbehebung für die vollständige Bereitstellung von /tmp für Adobe Commerce
description: Dieser Artikel bietet eine Lösung für den Fall, dass der "/tmp"-Berg voll ist, die Site möglicherweise ausfällt und Sie nicht in der Lage sind, SSH in einen Knoten einzufügen.
exl-id: e72d0f99-0060-474b-bb1c-2851896e1e43
feature: Storage
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# Fehlerbehebung für die vollständige Bereitstellung von /tmp für Adobe Commerce

Dieser Artikel bietet eine Lösung für den Fall, dass die `/tmp` -Bereitstellung voll ist, die Site möglicherweise ausfällt und Sie nicht in der Lage sind, SSH in einen Knoten einzubinden.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.3.0 - 2.3.6-p1, 2.4.0 - 2.4.2

## Problem

Wenn der `/tmp`-Reittier voll ist, kann dies zu einer Reihe möglicher Symptome führen, darunter die folgenden Fehler:

* *SQLSTATE[HY000]: Allgemeiner Fehler: 3 Fehler beim Schreiben der Datei*
* *Fehlercode: 28*
* *Auf dem Gerät verbleibender Speicherplatz (28)*
* *error session_start(): failed: No space left on device*
* *FEHLER 1 (HY000): Kann nicht in Datei &quot;/tmp/*&quot;erstellen/schreiben
* *SQL-Fehler: 3, SQLStat: HY000*
* *Allgemeiner Fehler: 1021 Festplatte voll (/tmp)*
* *Der Zugriff auf den Knoten über SSH ist nicht möglich:*
  *bash: Kann keine temporäre Datei für dieses Dokument erstellen: Auf dem Gerät ist kein Speicherplatz mehr vorhanden*
* *errno: 28 &quot;Auf dem Gerät ist kein Platz mehr&quot;*
* *mysqld: Datenträger ist voll geschrieben &#39;/tmp&#39;*
* *[ERROR] mysqld: Disk full (/tmp)*
* *SQLSTATE[HY000]: Allgemeiner Fehler: 1 Kann nicht in Datei &#39;/tmp/&#39;* erstellen/schreiben
* *SQLSTATE[HY000]: Allgemeiner Fehler: 23 Nicht genügend Ressourcen beim Öffnen der Datei &#39;/tmp/&#39;*
* *Fehlercode: 24 &quot;Zu viele geöffnete Dateien&quot;*
* *Fehler erhalten: 23: Nicht genügend Ressourcen beim Öffnen der Datei*


<u>Zu reproduzierende Schritte:</u>

Um zu überprüfen, wie voll das `/tmp` -Mounten ist, wechseln Sie in der CLI zu `/tmp` und führen Sie den folgenden Befehl aus:

```bash
 df -h
```

<u>Erwartetes Ergebnis</u>:

Weniger als 80 %.

<u>Tatsächliches Ergebnis</u>:

Etwa 100 %.

## Ursache

Das `/tmp` -Mount hat zu viele Dateien, die durch Folgendes verursacht werden können:

* Ungültige SQL-Abfragen, die große und/oder zu viele temporäre Tabellen generieren.
* Dienste, die in den Ordner &quot;`/tmp`&quot;schreiben.
* Datenbank-Sicherungen/Dumps, die im Verzeichnis `/tmp` verbleiben.

## Lösung

Es gibt Dinge, die Sie tun können, um einmal Speicherplatz freizugeben, und es gibt Best Practices, die verhindern würden, dass `\tmp` voll wird.

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

Stellen Sie sicher, dass Use% &lt;70% ist. Knoten werden mit Dateien korreliert. Wenn Sie Dateien aus der Partition entfernen, werden Sie Inodes freigeben.

### Speicherplatz einchecken und freigeben

Es gibt mehrere Dienste, die Dateien möglicherweise in `/tmp` speichern.

#### Sichern und Freigeben von MySQL-Speicherplatz

Befolgen Sie die Anweisungen unter [MySQL-Speicherplatz ist auf Adobe Commerce in der Cloud-Infrastruktur gering > Überprüfen und freigeben Sie Speicherplatz](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md#check_and_free) in unserer Support-Wissensdatenbank.

#### Überprüfen von Elasticsearch-Heapdumps

>[!WARNING]
>
>Heapdumps enthalten Protokollierungsinformationen, die für die Untersuchung von Problemen nützlich sein können. Sie sollten sie mindestens 10 Tage lang an einem anderen Speicherort speichern.

Entfernen Sie Heapdumps (`*.hprof`) mithilfe der System-Shell:

```bash
find /tmp/*.hprof -type f -delete
```

Wenn Sie nicht berechtigt sind, Dateien zu löschen, die von einem anderen Benutzer erstellt wurden (in diesem Fall Elasticsearch), aber Sie feststellen, dass die Dateien groß sind, erstellen Sie bitte ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um sie zu bearbeiten.[

#### Überprüfen von Datenbank-Dumps/Sicherungen

>[!WARNING]
>
>Datenbanksicherungen werden in der Regel zu einem bestimmten Zweck erstellt. Wenn Sie nicht sicher sind, ob die Datei weiterhin benötigt wird, sollten Sie sie an einen anderen Speicherort verschieben, anstatt sie zu löschen.

Überprüfen Sie `/tmp` auf `.sql` - oder `.sql.gz` -Dateien und bereinigen Sie sie. Diese wurden möglicherweise während der Sicherung oder beim manuellen Erstellen von Datenbank-Dumps mit dem `mysqldump` -Tool von ece-Tools erstellt.

### Best Practices

Um zu vermeiden, dass Probleme mit `/tmp` vollständig auftreten, befolgen Sie die folgenden Empfehlungen:

* Verwenden Sie MySQL nicht für die Suche. Elasticsearch für die Suche entfällt in der Regel die Notwendigkeit für die meisten schweren temporären Tabellen. Siehe [Konfigurieren von Adobe Commerce für die Verwendung von Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/configure-search-engine) in unserer Entwicklerdokumentation.
* Vermeiden Sie die Ausführung der `SELECT`-Abfrage für Spalten ohne Indizes, da diese eine große Menge temporären Speicherplatz beanspruchen. Sie können auch die Indizes hinzufügen.
* Erstellen Sie einen Cron zum Bereinigen von `/tmp`, indem Sie den folgenden Befehl in der CLI ausführen:

  ```bash
  sudo find /tmp -type f -atime +10 -delete
  ```

## Verwandtes Lesen

[MySQL-Speicherplatz auf Adobe Commerce in der Cloud-Infrastruktur ist gering](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) in unserer Support-Wissensdatenbank.
