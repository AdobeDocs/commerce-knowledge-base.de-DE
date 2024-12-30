---
title: '[!DNL Cron] Auftrag steckt im Status **Wird ausgeführt** fest'
description: Dieser Artikel bietet Lösungen für den Fall,  [!DNL cron]  Adobe Commerce-Aufträge die Ausführung nicht abschließen und in einem „laufenden“ Status verbleiben, der die Ausführung  [!DNL cron]  anderen Aufträge verhindert. Dies kann verschiedene Ursachen haben, z. B. Netzwerkprobleme, Anwendungsabstürze oder Probleme bei der erneuten Bereitstellung.
exl-id: 11e01a2b-2fcf-48c2-871c-08f29cd76250
feature: Configuration
role: Developer
source-git-commit: 08a241131453725a86eda5f267a209e6705da2e3
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# [!DNL Cron] Auftrag steckt im Status „Wird ausgeführt“ fest

Dieser Artikel bietet Lösungen für den Fall, dass Adobe Commerce [!DNL cron]-Aufträge nicht abgeschlossen werden und weiterhin den Status „Wird ausgeführt“ aufweisen, was die Ausführung anderer [!DNL cron] verhindert. Dies kann verschiedene Ursachen haben, z. B. Netzwerkprobleme, Anwendungsabstürze oder Probleme bei der erneuten Bereitstellung.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur, alle Versionen

## Symptom {#symptom}

Zu den Symptomen [!DNL cron] Aufträge, die zurückgesetzt werden müssen, gehören:

* In der `cron_schedule`-Warteschlange werden viele Aufträge angezeigt
* Site-Leistung beginnt zu sinken
* Vorgänge werden nicht planmäßig ausgeführt

## Lösungen {#solutions}

### Lösung zum gleichzeitigen Anhalten [!DNL cron] Aufträge {#solution-stop-all-crons-at-once}

>[!WARNING]
>
>Wenn Sie diesen Befehl ohne die Option `--job-code` ausführen, werden *alle* [!DNL cron] Aufträge zurückgesetzt, einschließlich der derzeit ausgeführten Aufträge. Daher empfehlen wir die Verwendung nur in Ausnahmefällen, z. B. nachdem Sie überprüft haben, dass alle [!DNL cron] Aufträge zurückgesetzt werden müssen. Bei der erneuten Bereitstellung wird dieser Befehl standardmäßig ausgeführt, um [!DNL cron] Aufträge zurückzusetzen, damit sie nach der Sicherung der Umgebung ordnungsgemäß wiederhergestellt werden. Vermeiden Sie diese Lösung, wenn Indexer ausgeführt werden.

Um dieses Problem zu beheben, müssen Sie den/die [!DNL cron] Auftrag/Aufträge mit dem Befehl `cron:unlock` zurücksetzen. Dieser Befehl ändert den Status des [!DNL cron] in der Datenbank und beendet den Vorgang erzwungen, damit andere geplante Aufträge fortgesetzt werden können.

1. Öffnen Sie ein Terminal und verwenden Sie Ihre [SSH](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections)Schlüssel, um eine Verbindung zur betroffenen Umgebung herzustellen.
1. Abrufen der MySQL-Datenbankanmeldeinformationen:    ```shell    echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp    ```
1. Stellen Sie mithilfe von `mysql` eine Verbindung zur Datenbank her:    ```shell    mysql -hdatabase.internal -uuser -ppassword main    ```
1. `main` auswählen:    ```shell    use main    ```
1. Alle laufenden [!DNL cron] Aufträge suchen:    ```shell    SELECT * FROM cron_schedule WHERE status = 'running';    ```
1. Kopieren Sie die `job_code` eines Auftrags, der länger als üblich ausgeführt wird.
1. Verwenden Sie die Zeitplan-IDs aus dem vorherigen Schritt, um bestimmte [!DNL cron] zu entsperren:    ```shell    ./vendor/bin/ece-tools cron:unlock --job-code=<job_code_1> [... --job-code=<job_code_x>]    ```

### Lösung zum Anhalten einer einzelnen [!DNL cron] {#solution-stop-a-single-cron}

1. Öffnen Sie ein Terminal und verwenden Sie Ihre [SSH](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections)Schlüssel, um eine Verbindung zur betroffenen Umgebung herzustellen.
1. Überprüfen Sie Aufgaben mit langer Laufzeit mithilfe des folgenden Befehls:

   ```date; ps aux | grep '[%]CPU\|cron\|magento\|queue' | grep -v 'grep\|cron -f'```

1. In der Ausgabe werden Sie wie in der Beispielausgabe unten das aktuelle Datum und die Liste der Prozesse sehen. Die Spalte `START` zeigt die Startzeit oder das Datum des Vorgangs an:

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

1. Wenn [!DNL cron] Aufträge mit langer Laufzeit angezeigt werden, die den Bereitstellungsprozess blockieren können, können Sie den Vorgang mit dem Befehl `kill` beenden. Sie können die **Prozess-ID** (in der `PID` Spalte gefunden) identifizieren und diese `PID` dann in den Befehl zum Beenden des Prozesses einfügen.
Der **Kill process**-Befehl lautet:

   ```kill -9 <PID>```

1. Wenn Sie eine erneute Bereitstellung versuchen, können Sie die Bereitstellung dann erneut durchführen.
