---
title: Erstellen eines Datenbank-Dump auf Adobe Commerce in der Cloud-Infrastruktur
description: In diesem Artikel werden die möglichen (und empfohlenen) Möglichkeiten zum Erstellen eines Datenbank-Dump (DB) in Adobe Commerce auf der Cloud-Infrastruktur erläutert.
exl-id: 4a2e54ac-8d65-4e51-8337-08f9748dc6c0
feature: Cloud
source-git-commit: 96b145a1f76c296907da96fd97c7a8f7778463f8
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Erstellen eines Datenbank-Dump auf Adobe Commerce in der Cloud-Infrastruktur

In diesem Artikel werden die möglichen (und empfohlenen) Möglichkeiten zum Erstellen eines Datenbank-Dump (DB) in Adobe Commerce auf der Cloud-Infrastruktur erläutert.

Sie müssen nur eine Variante (Option) verwenden, um Ihre Datenbank zu entladen. Diese Optionen gelten für jeden Umgebungstyp (Integration, Staging, Produktion) und jeden Plan (Starterplanarchitektur für Adobe Commerce in der Cloud-Infrastruktur und Planarchitektur für Adobe Commerce in der Cloud-Infrastruktur).

## Voraussetzung: SSH in Ihre Umgebung

Um Ihre DB mit einer in diesem Artikel besprochenen Variante auf Adobe Commerce in der Cloud-Infrastruktur zu entladen, müssen Sie zunächst [SSH in Ihre Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).

>[!WARNING]
>
>Unabhängig davon, ob Sie Option 1 oder Option 2 wählen, führen Sie den Befehl außerhalb der Spitzenzeiten für einen sekundären Datenbankknoten aus.

## Option 1: db-dump (**ECE-Tools; empfohlen**)

Sie können Ihre Datenbank mit dem Befehl [ECE-Tools](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) entladen:

```php
vendor/bin/ece-tools db-dump
```

Dies ist die empfohlene und sicherste Option.

Siehe [Dump Ihrer Datenbank (ECE-Tools)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/database-dump.html) in unserem Handbuch zu Commerce in Cloud Infrastructure.

## Option 2: mariadb-dump (oder mysqldump für ältere Versionen)

+++<b>Für neuere MariaDB-Versionen (11.x und höher)</b>

Ab MariaDB 11.0.1 wird der `mysqldump` Symlink nicht mehr unterstützt. Es wird empfohlen, stattdessen `mariadb-dump` zu verwenden.

Weitere Informationen finden Sie unter [mariadb-dump-Client-Dienstprogramm](https://mariadb.com/docs/server/clients-and-utilities/backup-restore-and-import-clients/mariadb-dump).

+++

+++<b>Für ältere MariaDB-Versionen</b> 

Wenn Sie eine ältere MariaDB-Version verwenden, in der `mariadb-dump` nicht verfügbar ist, können Sie Ihre Datenbank mithilfe des nativen MySQL-`mysqldump`-Befehls entladen.

>[!WARNING]
>
>Führen Sie diesen Befehl nicht für den Datenbank-Cluster aus. Der Cluster unterscheidet nicht, ob er für die primäre Datenbank oder für eine sekundäre Datenbank ausgeführt wird. Wenn der Cluster diesen Befehl für die primäre Instanz ausführt, kann die Datenbank keine Schreibvorgänge ausführen, bis der Dump abgeschlossen ist, was sich auf die Leistung und Website-Stabilität auswirken könnte.

Der gesamte Befehl könnte wie folgt aussehen:

```sql
mysqldump -h <host> -u <username> -p <password> --single-transaction <db_name> | gzip > /tmp/<dump_name>.sql.gz
```

Das Datenbank-Backup, das durch Ausführen des `mysqldump`-Befehls erstellt und in `\tmp` gespeichert wurde, sollte von diesem Speicherort verschoben werden. Es sollte keinen Speicherplatz in `\tmp` beanspruchen (was zu Problemen führen könnte).

+++

Um Ihre DB-Anmeldeinformationen (Host, Benutzername und Kennwort) abzurufen, können Sie die `MAGENTO_CLOUD_RELATIONSHIPS` Umgebungsvariable aufrufen:

```
echo $MAGENTO_CLOUD_RELATIONSHIPS |base64 --d |json_pp
```

**Verwandte Dokumentation:**

* [mysqldump - Ein Datenbanksicherungsprogramm](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) in der offiziellen MySQL-Dokumentation.
* [Cloud-spezifische Variablen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html) (siehe `MAGENTO_CLOUD_RELATIONSHIPS`) in unserem Handbuch zu Commerce in Cloud-Infrastrukturen .
