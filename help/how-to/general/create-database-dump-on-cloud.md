---
title: Erstellen eines Datenbank-Dump auf Adobe Commerce in der Cloud-Infrastruktur
description: In diesem Artikel werden die möglichen (und empfohlenen) Methoden zum Erstellen eines Datenbank-Dump (DB) auf Adobe Commerce in der Cloud-Infrastruktur erläutert.
exl-id: 4a2e54ac-8d65-4e51-8337-08f9748dc6c0
feature: Cloud
source-git-commit: 0948b2a94ee4f2a355e7c024a09929f0ad223783
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Erstellen eines Datenbank-Dump auf Adobe Commerce in der Cloud-Infrastruktur

In diesem Artikel werden die möglichen (und empfohlenen) Methoden zum Erstellen eines Datenbank-Dump (DB) auf Adobe Commerce in der Cloud-Infrastruktur erläutert.

Sie müssen nur eine Variante (Option) verwenden, um Ihre DB zu komprimieren. Diese Optionen gelten für alle Umgebungstypen (Integration, Staging, Produktion) und alle Pläne (Adobe Commerce auf der Starter-Planarchitektur der Cloud-Infrastruktur und Adobe Commerce auf der Planarchitektur von Cloud Infrastructure Pro).

## Voraussetzung: SSH in Ihrer Umgebung

Um Ihre DB auf Adobe Commerce in einer Cloud-Infrastruktur mit einer beliebigen Variante zu speichern, die in diesem Artikel besprochen wird, müssen Sie zunächst [SSH in Ihrer Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).

>[!WARNING]
>
>Unabhängig davon, ob Sie Option 1 oder Option 2 auswählen, führen Sie den Befehl während der Nebenzeiten außerhalb der Spitzenzeiten für einen sekundären Datenbankknoten aus.

## Option 1: db-dump (**Eichwerkzeuge; empfohlen**)

Sie können Ihre DB mit dem [ECE-Tools](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) command:

```php
vendor/bin/ece-tools db-dump
```

Dies ist die empfohlene und sicherste Option.

Siehe [Datenbank abrufen (ECE-Tools)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/database-dump.html) in unserem Commerce on Cloud Infrastructure Guide.

## Option 2: mysqldump

>[!WARNING]
>
>Führen Sie diesen Befehl nicht für den Datenbankcluster aus. Der Cluster unterscheidet nicht, ob er mit der primären Datenbank oder einer sekundären Datenbank ausgeführt wird. Wenn der Cluster diesen Befehl für die primäre Instanz ausführt, kann die Datenbank bis zum Abschluss des Dumps keine Schreibvorgänge ausführen und könnte sich auf die Leistung und Site-Stabilität auswirken.

Sie können Ihre DB mit der nativen MySQL-Software komprimieren. `mysqldump` Befehl.

Der gesamte Befehl könnte wie folgt aussehen:

```sql
mysqldump -h <host> -u <username> -p <password> --single-transaction <db_name> | gzip > /tmp/<dump_name>.sql.gz
```

Die durch Ausführen der `mysqldump` Befehl und gespeichert in `\tmp`von diesem Speicherort verschoben werden. Es sollte keinen Speicherplatz in `\tmp` (was zu Problemen führen kann).

Um Ihre DB-Anmeldeinformationen (Host, Benutzername und Kennwort) abzurufen, können Sie die `MAGENTO_CLOUD_RELATIONSHIPS` Umgebungsvariable:

```
echo $MAGENTO_CLOUD_RELATIONSHIPS |base64 --d |json_pp
```

**Verwandte Dokumentation:**

* [mysqldump - Ein Datenbanksicherungsprogramm](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) in der offiziellen MySQL-Dokumentation.
* [Cloud-spezifische Variablen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html) (siehe `MAGENTO_CLOUD_RELATIONSHIPS`) in unserem Commerce on Cloud Infrastructure Guide.
