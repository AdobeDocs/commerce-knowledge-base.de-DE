---
title: '[!DNL Cron] Aufgaben Sperren von Aufgaben aus anderen Gruppen'
description: Dieser Artikel bietet eine Lösung für das Adobe Commerce-Problem mit der Cloud-Infrastruktur im Zusammenhang mit bestimmten langfristigen Aufträgen [!DNL cron]  die andere Aufträge  [!DNL cron] .
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# [!DNL Cron] Aufgaben Sperren von Aufgaben aus anderen Gruppen

Dieser Artikel bietet eine Lösung für das Adobe Commerce-Problem mit der Cloud-Infrastruktur im Zusammenhang mit bestimmten langfristigen [!DNL cron], die andere [!DNL cron] blockieren.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur Pro Planarchitektur
* Vorher als Mai 2019 an Bord

## Problem

Wenn Sie in Adobe Commerce für Cloud Manager komplexe [!DNL cron] (langfristige Aufgaben) haben, können diese andere Aufgaben für die Ausführung sperren. Beispielsweise indiziert die Aufgabe der Indexer ungültig gemachte Indexer neu. Es kann einige Stunden dauern, bis der Vorgang abgeschlossen ist, und es werden andere standardmäßige [!DNL cron] wie das Senden von E-Mails, das Generieren von Sitemaps, Kundenbenachrichtigungen und andere benutzerdefinierte Aufgaben gesperrt.

<u>Symptome</u>:

Die von [!DNL cron] Aufträgen ausgeführten Prozesse werden nicht ausgeführt. Beispielsweise werden Produktaktualisierungen stundenlang nicht angewendet oder Kunden melden, dass sie keine E-Mails erhalten.

Wenn Sie die `cron_schedule` Datenbanktabelle öffnen, werden die Aufträge mit dem Status `missed` angezeigt.

## Ursache

Zuvor wurde in unserer Cloud-Umgebung der Jenkins-Server zum Ausführen von [!DNL cron] verwendet. Jenkins führt nur jeweils eine Instanz eines Auftrags aus. Infolgedessen wird jeweils nur ein `bin/magento cron:run` ausgeführt.

## Lösung

1. Wenden Sie sich an den [Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)Support, um die selbstverwaltete [!DNL crons] aktivieren zu lassen.
1. Bearbeiten Sie die `.magento.app.yaml` im Stammverzeichnis des Codes für Adobe Commerce in der [!DNL Git]. Folgendes hinzufügen:

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. Speichern Sie die Datei und übertragen Sie Aktualisierungen auf die Staging- und Produktionsumgebungen (auf die gleiche Weise wie bei Integrationsumgebungen).

>[!NOTE]
>
>Es ist nicht erforderlich, alte [!DNL cron]-Konfigurationen, in denen mehrere `cron:run` vorhanden sind, auf den neuen [!DNL cron]-Zeitplan zu übertragen. Die reguläre `cron:run`-Aufgabe, die wie oben beschrieben hinzugefügt wurde, ist ausreichend. Es ist jedoch erforderlich, Ihre benutzerdefinierten Aufträge zu übertragen, falls vorhanden.

### Überprüfen Sie, ob Sie Self-Managed [!DNL cron] aktiviert haben (nur für Cloud Pro Staging und Produktion)

Um zu überprüfen, ob die selbst verwaltete [!DNL cron] aktiviert ist, führen Sie den `crontab -l` Befehl aus und beobachten Sie das Ergebnis:

* Die selbstverwaltete [!DNL cron] ist aktiviert, wenn Sie die Aufgaben wie die folgenden sehen können:

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* Die selbstverwaltete [!DNL cron] wird nicht aktiviert, wenn Sie die Aufgaben nicht sehen können und die Fehlermeldung *Sie dürfen dieses Programm nicht verwenden* erhalten.

>[!NOTE]
>
>Der oben genannte Befehl zur Überprüfung, ob die selbst verwaltete [!DNL cron] aktiviert ist, gilt nicht für einen Starter-Plan und in der Entwicklungs-/Integrationsumgebung.

## Verwandtes Lesen

* [Setup [!DNL cron] jobs](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) in unserer Entwicklerdokumentation
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
