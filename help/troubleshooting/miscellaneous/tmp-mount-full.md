---
title: Fehlerbehebung für die vollständige Bereitstellung von /tmp für Adobe Commerce
description: Dieser Artikel bietet eine Lösung für den Fall, dass der "/tmp"-Berg voll ist, die Site möglicherweise ausfällt und Sie nicht in der Lage sind, SSH in einen Knoten einzufügen.
exl-id: e72d0f99-0060-474b-bb1c-2851896e1e43
feature: Storage
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# Fehlerbehebung für die vollständige Bereitstellung von /tmp für Adobe Commerce

Dieser Artikel bietet eine Lösung für den Zeitpunkt, zu dem die Variable `/tmp` Die Bereitstellung ist voll, die Site kann heruntergefahren sein und Sie können SSH nicht in einen Knoten integrieren.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.3.0 - 2.3.6-p1, 2.4.0 - 2.4.2

## Problem

Die `/tmp` Wenn das Reittier voll ist, kann dies zu einer Reihe möglicher Symptome führen, darunter die folgenden Fehler:

* *SQLSTATE[HY000]: Allgemeiner Fehler: 3 Fehler beim Schreiben der Datei*
* *Fehler-Code: 28*
* *Auf dem Gerät verbleibender Speicherplatz (28)*
* *error session_start(): failed: No space left on device*
* *FEHLER 1 (HY000): Kann nicht in Datei &quot;/tmp/&quot;erstellen/schreiben*
* *SQL-Fehler: 3, SQLStat: HY000*
* *Allgemeiner Fehler: 1021 Festplatte voll (/tmp)*
* *Zugriff auf Knoten über SSH nicht möglich:*
  *bash: temporäre Datei für dieses Dokument kann nicht erstellt werden: Auf dem Gerät ist kein Speicherplatz mehr vorhanden*
* *errno: 28 &quot;Auf dem Gerät ist kein Speicherplatz mehr vorhanden&quot;*
* *mysqld: Datenträger ist voll geschrieben &#39;/tmp&#39;*
* *[FEHLER] mysqld: Disk full (/tmp)*
* *SQLSTATE[HY000]: Allgemeiner Fehler: 1 Kann nicht in Datei &#39;/tmp/&#39; erstellen/schreiben*
* *SQLSTATE[HY000]: Allgemeiner Fehler: 23 Nicht genügend Ressourcen beim Öffnen der Datei &#39;/tmp/&#39;*
* *Fehlercode: 24 &quot;Zu viele geöffnete Dateien&quot;*
* *Fehler erhalten: 23: Nicht genügend Ressourcen beim Öffnen der Datei*


<u>Zu reproduzierende Schritte:</u>

So prüfen Sie, wie voll die `/tmp` &quot;mounten&quot;ist, wechseln Sie in der CLI zu `/tmp` und führen Sie den folgenden Befehl aus:

```bash
 df -h
```

<u>Erwartetes Ergebnis</u>:

Weniger als 80 %.

<u>Tatsächliches Ergebnis</u>:

Etwa 100 %.

## Ursache

Die `/tmp` Das Mount hat zu viele Dateien, was durch Folgendes verursacht werden könnte:

* Ungültige SQL-Abfragen, die große und/oder zu viele temporäre Tabellen generieren.
* Dienste, die an die `/tmp` Verzeichnis.
* Datenbank-Backups/Dumps, die im `/tmp` Verzeichnis.

## Lösung

Es gibt Dinge, die Sie tun können, um etwas Speicherplatz einmal freizugeben, und es gibt Best Practices, die verhindern würden `\tmp` nicht voll werden.

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

Es gibt mehrere Dienste, die Dateien speichern können in `/tmp`.

#### Sichern und Freigeben von MySQL-Speicherplatz

Befolgen Sie die Anweisungen unter [MySQL-Speicherplatz ist in Adobe Commerce in der Cloud-Infrastruktur gering > Speichern und Freigeben von Speicherplatz](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md#check_and_free) in unserer Wissensdatenbank.

#### Überprüfen von Elasticsearch-Heapdumps

>[!WARNING]
>
>Heapdumps enthalten Protokollierungsinformationen, die für die Untersuchung von Problemen nützlich sein können. Sie sollten sie mindestens 10 Tage lang an einem anderen Speicherort speichern.

Heapdumps entfernen (`*.hprof`) unter Verwendung der System-Shell:

```bash
find /tmp/*.hprof -type f -delete
```

Wenn Sie nicht berechtigt sind, Dateien zu löschen, die von einem anderen Benutzer erstellt wurden (in diesem Fall Elasticsearch), aber Sie sehen, dass die Dateien groß sind, dann [Support-Ticket erstellen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) um mit ihnen umzugehen.

#### Überprüfen von Datenbank-Dumps/Sicherungen

>[!WARNING]
>
>Datenbanksicherungen werden in der Regel zu einem bestimmten Zweck erstellt. Wenn Sie nicht sicher sind, ob die Datei weiterhin benötigt wird, sollten Sie sie an einen anderen Speicherort verschieben, anstatt sie zu löschen.

Überprüfen `/tmp` für `.sql` oder `.sql.gz` und bereinigen Sie sie. Diese wurden möglicherweise während der Sicherung oder beim manuellen Erstellen von Datenbank-Dumps mithilfe des `mysqldump` -Tool.

### Best Practices

So vermeiden Sie Probleme mit `/tmp` befolgen Sie diese Empfehlungen:

* Verwenden Sie MySQL nicht für die Suche. Elasticsearch für die Suche entfällt in der Regel die Notwendigkeit für die meisten schweren temporären Tabellen. Siehe [Adobe Commerce für die Verwendung von Elasticsearch konfigurieren](https://devdocs.magento.com/guides/v2.2/config-guide/elasticsearch/configure-magento.html) in unserer Entwicklerdokumentation.
* Vermeiden Sie das Ausführen der `SELECT` Abfrage von Spalten ohne Indizes, da diese eine große Menge temporären Speicherplatz beanspruchen. Sie können auch die Indizes hinzufügen.
* Erstellen eines Crons zur Bereinigung `/tmp` durch Ausführen des folgenden Befehls in der CLI:

  ```bash
  sudo find /tmp -type f -atime +10 -delete
  ```

## Verwandtes Lesen

[MySQL-Speicherplatz in Adobe Commerce in der Cloud-Infrastruktur ist gering](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) in unserer Wissensdatenbank.
