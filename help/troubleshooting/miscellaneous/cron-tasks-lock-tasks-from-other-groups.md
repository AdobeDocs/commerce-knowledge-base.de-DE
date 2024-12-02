---
title: '[!DNL Cron] Aufgaben sperren Aufgaben von anderen Gruppen'
description: Dieser Artikel bietet eine Lösung für die Adobe Commerce zum Problem der Cloud-Infrastruktur im Zusammenhang mit bestimmten langfristigen [!DNL cron] Aufträgen, die andere [!DNL cron] Aufträge blockieren.
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# [!DNL Cron] Aufgaben sperren Aufgaben von anderen Gruppen

Dieser Artikel bietet eine Lösung für die Adobe Commerce zum Problem der Cloud-Infrastruktur im Zusammenhang mit bestimmten langfristigen [!DNL cron] Aufträgen, die andere [!DNL cron] Aufträge blockieren.

## Betroffene Produkte und Versionen

* Adobe Commerce on Cloud Infrastructure Pro-Planarchitektur
* Vor Mai 2019 an Bord

## Problem

Wenn Sie in Adobe Commerce for Cloud komplexe [!DNL cron] Aufgaben (langfristige Aufgaben) haben, werden diese möglicherweise andere Aufgaben für die Ausführung sperren. Beispielsweise werden durch die Aufgabe der Indexer invalidierte Indexer neu indiziert. Es kann einige Stunden dauern, bis andere standardmäßige [!DNL cron]-Aufträge, wie das Senden von E-Mails, das Generieren von Sitemaps, Kundenbenachrichtigungen und andere benutzerdefinierte Aufgaben, beendet werden.

<u>Symptome</u>:

Die von [!DNL cron] -Aufträgen ausgeführten Prozesse werden nicht ausgeführt. Beispielsweise werden Produktaktualisierungen nicht stundenlang angewendet oder Kunden melden, dass sie keine E-Mails erhalten.

Wenn Sie die Datenbanktabelle `cron_schedule` öffnen, sehen Sie die Aufträge mit dem Status `missed` .

## Ursache

Zuvor wurde in unserer Cloud-Umgebung der Jenkins-Server verwendet, um [!DNL cron] Aufträge auszuführen. Jenkins führt jeweils nur eine Instanz eines Auftrags aus. Folglich wird jeweils nur ein `bin/magento cron:run` -Prozess ausgeführt.

## Lösung

1. Wenden Sie sich an den [Adobe Commerce-Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) , damit die Self-Managed [!DNL crons] aktiviert ist.
1. Bearbeiten Sie die Datei &quot;`.magento.app.yaml`&quot; im Stammverzeichnis des Codes für Adobe Commerce in der Verzweigung &quot;[!DNL Git]&quot;. Fügen Sie Folgendes hinzu:

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. Speichern Sie die Datei und pushen Sie Aktualisierungen in den Staging- und Produktionsumgebungen (auf die gleiche Weise wie bei Integrationsumgebungen).

>[!NOTE]
>
>Es ist nicht erforderlich, alte [!DNL cron]-Konfigurationen zu übertragen, bei denen mehrere `cron:run` vorhanden sind, um den neuen [!DNL cron]-Zeitplan zu erhalten. Die normale `cron:run`-Aufgabe, die wie oben beschrieben hinzugefügt wurde, reicht aus. Es ist jedoch erforderlich, Ihre benutzerdefinierten Aufträge zu übertragen, falls vorhanden.

### Überprüfen Sie, ob Sie die selbst verwaltete [!DNL cron]-Funktion aktiviert haben (nur für Cloud Pro Staging und Produktion).

Um zu überprüfen, ob die selbst verwaltete [!DNL cron] aktiviert ist, führen Sie den Befehl `crontab -l` aus und beobachten Sie das Ergebnis:

* Self-managed [!DNL cron] ist aktiviert, wenn Sie die Aufgaben sehen können, wie die folgenden:

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* Die selbst verwaltete [!DNL cron]-Fehlermeldung &quot;*&quot;kann nicht angezeigt werden, wenn Sie die Aufgaben nicht sehen können und die Fehlermeldung &quot;* Sie dürfen dieses Programm nicht verwenden&quot; erhalten.

>[!NOTE]
>
>Der oben erwähnte Befehl, um zu überprüfen, ob die selbstverwaltete [!DNL cron] aktiviert ist, gilt nicht für einen Starter-Plan und die Entwicklungs-/Integrationsumgebung.

## Verwandtes Lesen

* [ Richten Sie  [!DNL cron] jobs](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) in unserer Entwicklerdokumentation ein.
* [Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung
