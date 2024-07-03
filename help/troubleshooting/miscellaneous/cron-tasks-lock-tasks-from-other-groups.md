---
title: Cron-Aufgaben sperren Aufgaben von anderen Gruppen
description: Dieser Artikel bietet eine Lösung für die Adobe Commerce in Bezug auf Cloud-Infrastrukturprobleme im Zusammenhang mit bestimmten langfristigen Cron-Aufträgen, die andere Cron-Aufträge blockieren.
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: faa80e8233438fc15781341b3a9d5325269d6d20
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Cron-Aufgaben sperren Aufgaben von anderen Gruppen

Dieser Artikel bietet eine Lösung für die Adobe Commerce in Bezug auf Cloud-Infrastrukturprobleme im Zusammenhang mit bestimmten langfristigen Cron-Aufträgen, die andere Cron-Aufträge blockieren.

## Betroffene Produkte und Versionen

* Adobe Commerce on Cloud Infrastructure Pro-Planarchitektur
* Vor Mai 2019 an Bord

## Problem

Wenn Sie in Adobe Commerce for Cloud komplexe Cron-Aufgaben (langfristige Aufgaben) haben, werden möglicherweise andere Aufgaben für die Ausführung gesperrt. Beispielsweise werden durch die Aufgabe der Indexer invalidierte Indexer neu indiziert. Es kann einige Stunden dauern, bis der Vorgang abgeschlossen ist. Außerdem werden andere standardmäßige Cron-Aufträge wie das Senden von E-Mails, das Generieren von Sitemaps, Kundenbenachrichtigungen und andere benutzerdefinierte Aufgaben gesperrt.

<u>Symptome</u>:

Die von Cron-Aufträgen ausgeführten Prozesse werden nicht ausgeführt. Beispielsweise werden Produktaktualisierungen nicht stundenlang angewendet oder Kunden melden, dass sie keine E-Mails erhalten.

Wenn Sie die `cron_schedule` Datenbanktabelle angezeigt werden, sehen Sie die Aufträge mit `missed` -Status.

## Ursache

Zuvor wurde in unserer Cloud-Umgebung der Jenkins-Server zum Ausführen von Cron-Aufträgen verwendet. Jenkins führt jeweils nur eine Instanz eines Auftrags aus; folglich wird es nur eine geben `bin/magento cron:run` -Prozess ausgeführt wird.

## Lösung

1. Kontakt [Adobe Commerce-Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) um selbstverwaltete Crons zu aktivieren.
1. Bearbeiten Sie die `.magento.app.yaml` im Stammverzeichnis des Codes für Adobe Commerce in der Git-Verzweigung. Fügen Sie Folgendes hinzu:

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. Speichern Sie die Datei und pushen Sie Aktualisierungen in den Staging- und Produktionsumgebungen (auf die gleiche Weise wie bei Integrationsumgebungen).

>[!NOTE]
>
>Es ist nicht erforderlich, alte Cron-Konfigurationen zu übertragen, bei denen mehrere `cron:run` für den neuen Cron-Zeitplan vorhanden sind; die reguläre `cron:run` -Aufgabe, wie oben beschrieben hinzugefügt, reicht aus. Es ist jedoch erforderlich, Ihre benutzerdefinierten Aufträge zu übertragen, falls vorhanden.

### Überprüfen Sie, ob die selbst verwaltete Cron-Funktion aktiviert ist (nur für Cloud Pro Staging und Produktion).

Um zu überprüfen, ob der selbst verwaltete Cron aktiviert ist, führen Sie den `crontab -l` -Befehl und beobachten Sie das Ergebnis:

* Selbstverwalteter Cron ist aktiviert, wenn Sie die Aufgaben sehen können, z. B.:

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* Der selbst verwaltete Cron ist nicht aktiviert, wenn Sie die Aufgaben nicht sehen und die *&quot;Sie dürfen dieses Programm nicht verwenden&quot;* Fehlermeldung.

>[!NOTE]
>
>Der oben erwähnte Befehl, um zu überprüfen, ob selbstverwalteter Cron aktiviert ist, gilt nicht für einen Starter-Plan und in der Entwicklungs-/Integrationsumgebung.

## Verwandtes Lesen

* [Einrichten von Cron-Aufträgen](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) in unserer Entwicklerdokumentation.
