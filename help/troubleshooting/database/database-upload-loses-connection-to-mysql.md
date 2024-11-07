---
title: Beim Hochladen der Datenbank wird die Verbindung zu MySQL unterbrochen
description: Dieser Artikel bietet eine Lösung für den Fall, dass der Datenbank-Upload die Verbindung zu MySQL verliert.
exl-id: 6051cea1-8292-4a81-8908-eb516cb4a32b
feature: Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Beim Hochladen der Datenbank wird die Verbindung zu MySQL unterbrochen

Dieser Artikel bietet eine Lösung für den Fall, dass der Datenbank-Upload die Verbindung zu MySQL verliert.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x

## Problem

Die Datenbank wird nicht in Primär-/Integrationszweige in Adobe Commerce in der Cloud Infrastructure Pro-Planarchitektur oder in einer Zweigstelle in Adobe Commerce in der Starter-Planarchitektur der Cloud-Infrastruktur hochgeladen, wobei das Symptom die Unfähigkeit ist, eine Verbindung herzustellen. Sie sehen diesen Fehler in der CLI.

```
web@ddc35c264bd89a72042f1f3e5a:~$ mysql -h database.internal -u user -p main
Enter password:
ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0 "Internal error/check (Not system error)"
```

## Ursache

Dies liegt in der Regel an mangelndem Speicherplatz für den Import der Datenbank.

## Lösung

Überprüfen Sie, ob nicht genügend Festplattenspeicher vorhanden ist. Führen Sie dazu den Befehl `netcat` in der CLI für den Datenbankanschluss 3306 aus. Wenn er voll ist, wird eine vollständige Meldung auf dem Datenträger ausgegeben:

```
web@ddc35c264bd89a72042f1f3e5a:~$ nc database.internal 3306
Database out of space
```

Sie müssen mehr Speicherplatz für die Datenbank in Ihrem `services.yaml` zuweisen und bereitstellen, wenn Sie Speicherplatz nicht verwendet haben. Anweisungen finden Sie unter [Service Disk Space](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#service-disk-space).

Hinweis: Im Pro-Architekturplan können Sie den zugewiesenen Speicherplatz auf Ihrer Partition überprüfen, indem Sie den folgenden Befehl ausführen: `df -h`

Erwarten Sie eine Ausgabe ähnlich der folgenden Ausgabe. In diesem Beispiel werden 10 GB des zugewiesenen 25 GB-Speichers verwendet, wobei 15 GB MySQL-Speicherplatz nicht verwendet werden.

```
f240jestone3wt@i-087r2a25fdac80726:~$ df -h|grep 'File\|xvd'
Filesystem                                         Size  Used Avail Use% Mounted on
/dev/xvda1                                          59G   15G   42G  26% /
/dev/xvdj                                           25G   10G   15G  41% /data/mysql
/dev/xvdi                                           25G   22G  2.6G  90% /data/exports
```

## Verwandtes Lesen

[Verwalten des Festplattenspeichers](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space) in unserer Entwicklerdokumentation
