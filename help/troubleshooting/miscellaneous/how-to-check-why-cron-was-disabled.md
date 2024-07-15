---
title: Überprüfen, warum [!DNL cron] deaktiviert war
description: In diesem Artikel finden Sie Lösungen zur Fehlerbehebung bei Problemen mit Cron in Adobe Commerce bei Cloud-Infrastrukturprodukten.
feature: Configuration
role: Developer
exl-id: d4d4a28d-3afa-4379-afc1-bc6250717784
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Überprüfen, warum [!DNL cron] deaktiviert wurde

In diesem Artikel finden Sie Lösungen zur Fehlerbehebung bei Problemen mit [!DNL cron] in Adobe Commerce bei Cloud-Infrastrukturprodukten.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle Versionen

## Problem

## Im Folgenden finden Sie Symptome von [!DNL cron] -Problemen:

Sie haben bemerkt, dass Ihr [!DNL cron] nicht ausgeführt wurde.
Beispiel: Sie sehen die folgenden Zeilen in der Datei &quot;`app/etc/env.php`&quot;:

```'cron' =>
  array (
    'enabled' => 0
  ),
```

Ein leeres Array würde bedeuten, dass der [!DNL cron] **enabled** ist:

```'cron' =>
  array (
  ),
```

## Ursachen

Es gibt mehrere Gründe, warum der [!DNL cron] derzeit nicht aktiv ist:

1. Die [!DNL cron] wurde aufgrund verpasster [!DNL OpCache] Einstellungen deaktiviert.
1. Das Infrastruktur-Team hat Ihre [!DNL cron] deaktiviert, da dies dazu führte, dass Ihre Site schlecht/schlecht ablief.
1. Die [!DNL cron] wurde nicht erneut aktiviert, da Ihre Bereitstellung fehlgeschlagen ist.

In einem der folgenden Abschnitte finden Sie eine Lösung für Ihr Problem.

## Lösungen

### Lösung für verpasste [!DNL OpCache] Einstellungen {#solution-missed-opcache-settings}

Siehe [[!DNL Cron] gestoppt aufgrund von falsch konfigurierten oder fehlenden [!DNL OpCache] Einstellungen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/crons-blocked-running-missing-opache-settings) in unserer Commerce-Wissensdatenbank.

### Lösung für Behinderte durch das Infrastrukturteam {#solution-disabled-by-infrastructure-team}

1. Überprüfen Sie Ihre vorherigen Support-Tickets, in denen Ihre Site ausfällt oder nicht reagiert.
1. Überprüfen Sie dann, ob das Infrastrukturteam angezeigt hat, dass es deaktiviert war.
1. Vergewissern Sie sich, dass Sie die vom Infrastrukturteam angesprochenen Probleme/Bedenken behoben haben.
1. Senden Sie eine [Support-Anfrage](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) , wenn Sie weitere Unterstützung benötigen, um die [!DNL cron] erneut zu aktivieren, und erklären Sie, wie Sie die vom Infrastrukturteam angegebenen Probleme gelöst haben.

### Lösung für fehlgeschlagene Bereitstellung {#solution-deployment-failed}

Überprüfen Sie die Bereitstellungsprotokolle:

* [ Anzeigen und Verwalten von Protokollen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations) in unserem Commerce on Cloud Infrastructure-Handbuch.
* [Überprüfen des Bereitstellungsprotokolls, ob die Cloud-Benutzeroberfläche in unserer Commerce-Wissensdatenbank *`log snipped`* error](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error) aufweist.

1. Wenn die Bereitstellung während des `setup:upgrade` -Schritts fehlgeschlagen war, wurde die [!DNL cron] nicht erneut aktiviert.
Beispiel: Sie sehen diese Zeile im Bereitstellungsprotokoll:

   ```The command "/bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade --keep-generated --ansi --no-interaction  | tee -a /app/$<project_id>/var/log/install_upgrade.log"" failed. Cache types config flushed successfully```

1. Andernfalls kann die Bereitstellung während einer anderen Phase fehlgeschlagen sein. Überprüfen Sie das Bereitstellungsprotokoll und stellen Sie sicher, dass beide Zeilen angezeigt werden (Beispiel unten). Wenn Sie nicht beide Zeilen sehen, die diesem im Protokoll ähnlich sind, bedeutet dies, dass die [!DNL cron] nicht erneut aktiviert wurde:

   ```  [2024-03-06T10:55:39.345564+00:00] INFO: Disable cron```<br>
...<br>
   ```  [2024-02-07T10:50:09.579005+00:00] INFO: Enable cron```

**Senden Sie eine [Support-Anfrage](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) , wenn Sie weitere Unterstützung benötigen.**
