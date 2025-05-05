---
title: Fehlerbehebung für die vollständige Einbindung von /tmp für Adobe Commerce
description: Dieser Artikel bietet eine Lösung für den Fall, dass die Bereitstellung von "/tmp“ voll ist, die Site möglicherweise ausgefallen ist und Sie nicht in der Lage sind, SSH in einen Knoten zu installieren.
exl-id: e72d0f99-0060-474b-bb1c-2851896e1e43
feature: Storage
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# Fehlerbehebung für die vollständige Einbindung von /tmp für Adobe Commerce

Dieser Artikel bietet eine Lösung für den Fall, dass die `/tmp`-Bereitstellung voll ist, die Site möglicherweise ausgefallen ist und Sie nicht in der Lage sind, SSH in einen -Knoten zu installieren.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.3.0 - 2.3.6-p1, 2.4.0 - 2.4.2

## Problem

Wenn die `/tmp` voll ist, kann dies zu einer Reihe möglicher Symptome führen, darunter die folgenden Fehler:

* *SQLSTATE[HY000]: Allgemeiner Fehler: 3 Fehler beim Schreiben der Datei*
* *Fehlercode: 28*
* *Kein Platz auf dem Gerät (28)*
* *error_session_start(): fehlgeschlagen: Kein Speicherplatz mehr auf dem Gerät*
* *ERROR 1 (HY000): Datei &#39;/tmp/* kann nicht erstellt/geschrieben werden
* *SQL-Fehler: 3, SQLState: HY000*
* *Allgemeiner Fehler: 1021 Festplatte voll (/tmp)*
* *Zugriff auf den Knoten über SSH nicht möglich:*
  *bash: Temporäre Datei für here-document kann nicht erstellt werden: Kein Speicherplatz mehr auf dem Gerät*
* *errno: 28 „No space left on device“*
* *mysqld: Datenträger ist voll schreibend &#39;/tmp&#39;*
* *[ERROR] mysqld: Datenträger voll (/tmp)*
* *SQLSTATE[HY000]: Allgemeiner Fehler: 1 In Datei &#39;/tmp/&#39; kann nicht erstellt/geschrieben werden*
* *SQLSTATE[HY000]: Allgemeiner Fehler: 23 von Ressourcen beim Öffnen der Datei &#39;/tmp/&#39;*
* *Fehlercode: 24 „Too Many Open Files“*
* *Fehler empfangen: 23: Nicht genügend Ressourcen beim Öffnen der Datei*


<u>Schritte zur Reproduktion:</u>

Um zu überprüfen, wie voll die `/tmp` ist, wechseln Sie in der CLI zu `/tmp` und führen Sie den folgenden Befehl aus:

```bash
 df -h
```

<u>Erwartetes Ergebnis</u>:

Weniger als 80 %.

<u>Tatsächliches </u>:

Rund 100 %.

## Ursache

Die `/tmp`-Bereitstellung enthält zu viele Dateien, was folgende Ursachen haben kann:

* Fehlerhafte SQL-Abfragen, die große und/oder zu viele temporäre Tabellen erzeugen.
* Dienste schreiben in das `/tmp`.
* Datenbank-Backups/-Dumps, die im `/tmp` verbleiben.

## Lösung

Es gibt Dinge, die Sie tun können, um einmal Speicherplatz freizugeben, und es gibt Best Practices, die verhindern würden, dass `\tmp` voll wird.

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

Überprüfen Sie, ob Verwendung % &lt; 70 % ist. Inodes sind mit Dateien korreliert. Wenn Sie Dateien aus der Partition entfernen, werden Inodes freigegeben.

### Überprüfen und Freigeben von Speicherplatz

Es gibt mehrere Services, die möglicherweise Dateien in `/tmp` speichern.

#### Überprüfen und Freigeben von MySQL-Speicherplatz

Befolgen Sie die Anweisungen in [MySQL Speicherplatz ist auf Adobe Commerce in der Cloud-Infrastruktur zu niedrig > Überprüfen Sie und geben Sie Speicherplatz frei](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md#check_and_free) in unserer Support-Wissensdatenbank.

#### Überprüfen von Elasticsearch-Heap-Dumps

>[!WARNING]
>
>Heap-Dumps enthalten Protokollierungsinformationen, die für die Untersuchung von Problemen nützlich sein können. Erwägen Sie, sie für mindestens 10 Tage an einem anderen Ort aufzubewahren.

Heap-Dumps (`*.hprof`) mit der System-Shell entfernen:

```bash
find /tmp/*.hprof -type f -delete
```

Wenn Sie nicht über die Berechtigung zum Löschen von Dateien verfügen, die von einem anderen Benutzer erstellt wurden (in diesem Fall von Elasticsearch), aber sehen, dass die Dateien groß sind, erstellen [ ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) um sie zu bearbeiten.

#### Überprüfen von Datenbank-Dumps/Backups

>[!WARNING]
>
>Datenbanksicherungen werden in der Regel zu einem bestimmten Zweck erstellt. Wenn Sie sich nicht sicher sind, ob die Datei weiterhin benötigt wird, verschieben Sie sie an einen anderen Speicherort, anstatt sie zu löschen.

Überprüfen Sie `/tmp` auf `.sql` oder `.sql.gz` Dateien und bereinigen Sie sie. Diese können von ECE-Tools während der Sicherung oder bei der manuellen Erstellung von Datenbank-Dumps mit dem `mysqldump`-Tool erstellt worden sein.

### Best Practices

Um Probleme mit `/tmp` zu vermeiden, die vollständig sind, befolgen Sie die folgenden Empfehlungen:

* Verwenden Sie MySQL nicht für die Suche. Elasticsearch für die Suche macht in der Regel die meisten der umfangreichen temporären Tabellenerstellungen überflüssig. Siehe [Adobe Commerce für die Verwendung von Elasticsearch konfigurieren](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/search/configure-search-engine) in unserer Entwicklerdokumentation.
* Vermeiden Sie das Ausführen der `SELECT` Abfrage für Spalten ohne Indizes, da dies viel temporären Speicherplatz beansprucht. Sie können auch die Indizes hinzufügen.
* Erstellen Sie einen Cron, um `/tmp` zu bereinigen, indem Sie den folgenden Befehl in der CLI ausführen:

  ```bash
  sudo find /tmp -type f -atime +10 -delete
  ```

## Verwandtes Lesen

[In unserer Support-Wissensdatenbank ist wenig Speicherplatz auf der Adobe Commerce-](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) vorhanden.
