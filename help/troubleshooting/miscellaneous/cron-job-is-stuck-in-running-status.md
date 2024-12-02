---
title: '[!DNL Cron] Auftrag ist im Status "running**"stecken geblieben'
description: Dieser Artikel bietet Lösungen für den Fall, dass Adobe Commerce [!DNL cron] Aufträge nicht abgeschlossen werden und in einem "laufenden"Status bestehen bleiben, was verhindert, dass andere [!DNL cron] Aufträge ausgeführt werden. Dies kann verschiedene Gründe haben, z. B. Netzwerkprobleme, Anwendungsabstürze oder Probleme bei der Neubereitstellung.
exl-id: 11e01a2b-2fcf-48c2-871c-08f29cd76250
feature: Configuration
role: Developer
source-git-commit: 08a241131453725a86eda5f267a209e6705da2e3
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# [!DNL Cron] Auftrag ist im Status &quot;Wird ausgeführt&quot; stecken

Dieser Artikel bietet Lösungen für den Fall, dass Adobe Commerce [!DNL cron]-Aufträge nicht abgeschlossen werden und in einem &quot;laufenden&quot;Status verbleiben, was verhindert, dass andere [!DNL cron] -Aufträge ausgeführt werden. Dies kann verschiedene Gründe haben, z. B. Netzwerkprobleme, Anwendungsabstürze oder Probleme bei der Neubereitstellung.

## Betroffene Produkte und Versionen

Adobe Commerce in der Cloud-Infrastruktur, alle Versionen

## Symptom {#symptom}

Zu den Symptomen von [!DNL cron] Aufträgen, die zurückgesetzt werden müssen, gehören:

* Eine große Anzahl von Aufträgen wird in der `cron_schedule`-Warteschlange angezeigt
* Die Site-Leistung nimmt ab
* Aufträge werden nicht planmäßig ausgeführt

## Lösungen {#solutions}

### Lösung zum gleichzeitigen Beenden aller [!DNL cron] Aufträge {#solution-stop-all-crons-at-once}

>[!WARNING]
>
>Wenn Sie diesen Befehl ohne die Option `--job-code` ausführen, werden alle *2} [!DNL cron] Aufträge zurückgesetzt, einschließlich der derzeit ausgeführten Aufträge. Daher empfehlen wir, ihn nur in Ausnahmefällen zu verwenden, z. B. nachdem Sie überprüft haben, dass alle [!DNL cron] Aufträge zurückgesetzt werden müssen.* Bei der erneuten Bereitstellung wird dieser Befehl standardmäßig ausgeführt, um [!DNL cron] Aufträge zurückzusetzen, sodass sie nach der Sicherung der Umgebung ordnungsgemäß abgerufen werden. Vermeiden Sie die Verwendung dieser Lösung, wenn Indexer ausgeführt werden.

Um dieses Problem zu beheben, müssen Sie die [!DNL cron] Aufträge mit dem Befehl `cron:unlock` zurücksetzen. Mit diesem Befehl wird der Status des [!DNL cron] -Auftrags in der Datenbank geändert und der Auftrag wird forciert beendet, damit andere geplante Aufträge fortgesetzt werden können.

1. Öffnen Sie ein Terminal und verwenden Sie Ihre [SSH-Schlüssel](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections), um eine Verbindung zur betroffenen Umgebung herzustellen.
1. Rufen Sie die Anmeldeinformationen der MySQL-Datenbank ab:    ```shell    echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp    ```
1. Stellen Sie mithilfe von `mysql` eine Verbindung zur Datenbank her:    ```shell    mysql -hdatabase.internal -uuser -ppassword main    ```
1. Wählen Sie die Datenbank `main` aus:    ```shell    use main    ```
1. Suchen Sie alle ausgeführten [!DNL cron] Aufträge:    ```shell    SELECT * FROM cron_schedule WHERE status = 'running';    ```
1. Kopieren Sie die `job_code` eines Auftrags, der länger als üblich ausgeführt wird.
1. Verwenden Sie die Zeitplan-IDs aus dem vorherigen Schritt, um bestimmte [!DNL cron] Aufträge zu entsperren:    ```shell    ./vendor/bin/ece-tools cron:unlock --job-code=<job_code_1> [... --job-code=<job_code_x>]    ```

### Lösung zum Anhalten einer einzelnen [!DNL cron] {#solution-stop-a-single-cron}

1. Öffnen Sie ein Terminal und verwenden Sie Ihre [SSH-Schlüssel](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections), um eine Verbindung zur betroffenen Umgebung herzustellen.
1. Überprüfen Sie langwierige Aufgaben mit dem folgenden Befehl:

   ```date; ps aux | grep '[%]CPU\|cron\|magento\|queue' | grep -v 'grep\|cron -f'```

1. Wie in der Beispielausgabe unten sehen Sie in der Ausgabe das aktuelle Datum und die Liste der Prozesse. Die Spalte `START` zeigt die Startzeit oder das Datum des Prozesses an:

   ```
   Wed May  8 22:41:31 UTC 2019
   USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
   root       590  0.0  0.0  27528  2768 ?        Ss   Jan15   0:49 /usr/sbin/cron -f
   bxc2qly+ 25855  0.0  0.0  23724  2184 ?        S    20:51   0:00 logger -d -u /run/bxc2qlykqhbqe_stg-cron.sock -p cron.info -s -t cron-bxc2qlykqhbqe_stg-bxc2qlykqhbqe_stg
   bxc2qly+ 25860 57.7  1.3 584220 222692 ?       S    20:51   0:02 php bin/magento cron:run
   bxc2qly+ 25863  0.0  0.0  23724  2472 ?        S    20:51   0:00 logger -d -u /run/bxc2qlykqhbqe-cron.sock -p cron.info -s -t cron-bxc2qlykqhbqe-bxc2qlykqhbqe
   bxc2qly+ 25876 53.0  0.6 475472 111468 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25878 57.0  0.6 475472 112080 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=staging --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25880 50.5  0.6 475472 111312 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=catalog_event --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25882 48.5  0.6 475472 111220 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=consumers --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25884 50.5  0.6 475472 111372 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=ddg_automation --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25890 32.5  0.6 475368 110672 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=staging --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25892 34.5  0.6 475472 110724 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=catalog_event --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25894 31.5  0.6 475368 110136 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=consumers --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25896 29.0  0.6 475320 109876 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=ddg_automation --bootstrap=standaloneProcessStarted=1
   ```

1. Wenn Sie eine lange Ausführung von [!DNL cron] Aufträgen sehen, die den Prozess der Blockbereitstellung auslösen können, können Sie den Prozess mit dem Befehl `kill` beenden. Sie können die **Prozess-ID** (Spalte `PID` gefunden) identifizieren und diese `PID` dann in den Befehl einfügen, um den Prozess abzubrechen.
Der Befehl **kill process** lautet:

   ```kill -9 <PID>```

1. Anschließend können Sie die Bereitstellung erneut durchführen, wenn Sie versuchen, die Bereitstellung erneut durchzuführen.
