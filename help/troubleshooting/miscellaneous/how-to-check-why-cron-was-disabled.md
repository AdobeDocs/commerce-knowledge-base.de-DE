---
title: Überprüfen der Gründe [!DNL cron] war deaktiviert
description: In diesem Artikel finden Sie Lösungen zur Fehlerbehebung bei Problemen mit Cron in Adobe Commerce bei Cloud-Infrastrukturprodukten.
feature: Configuration
role: Developer
exl-id: d4d4a28d-3afa-4379-afc1-bc6250717784
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Überprüfen der Gründe [!DNL cron] war deaktiviert

Dieser Artikel bietet Lösungen zur Fehlerbehebung bei Problemen mit [!DNL cron] in Adobe Commerce zu Cloud-Infrastrukturprodukten.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle Versionen

## Problem

## Die folgenden Symptome [!DNL cron] Probleme:

Sie haben bemerkt, dass Ihre [!DNL cron] nicht lief.
Zum Beispiel sehen Sie die folgenden Zeilen im `app/etc/env.php` Datei:

```'cron' =>
  array (
    'enabled' => 0
  ),
```

Ein leeres Array würde bedeuten, dass die Variable [!DNL cron] is **enabled**:

```'cron' =>
  array (
  ),
```

## Ursachen

Es gibt mehrere Gründe, warum die [!DNL cron] ist derzeit nicht aktiv:

1. Die [!DNL cron] aufgrund von verpassten [!DNL OpCache] -Einstellungen.
1. Das Infrastrukturteam hat Ihre [!DNL cron], da dies dazu führte, dass Ihre Site nur schlecht ablief bzw. herunterging.
1. Die [!DNL cron] nicht erneut aktiviert wurde, da Ihre Implementierung fehlgeschlagen ist.

In einem der folgenden Abschnitte finden Sie eine Lösung für Ihr Problem.

## Lösungen

### Lösung für verpasste [!DNL OpCache] settings {#solution-missed-opcache-settings}

Siehe [[!DNL Cron] aufgrund von falsch Konfiguration oder fehlenden [!DNL OpCache] settings](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/crons-blocked-running-missing-opache-settings) in unserer Commerce-Wissensdatenbank.

### Lösung für Behinderte durch das Infrastrukturteam {#solution-disabled-by-infrastructure-team}

1. Überprüfen Sie Ihre vorherigen Support-Tickets, in denen Ihre Site ausfällt oder nicht reagiert.
1. Überprüfen Sie dann, ob das Infrastrukturteam angezeigt hat, dass es deaktiviert war.
1. Vergewissern Sie sich, dass Sie die vom Infrastrukturteam angesprochenen Probleme/Bedenken behoben haben.
1. Senden einer [Support-Anfrage](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) wenn Sie weitere Unterstützung benötigen, um die [!DNL cron] und erläutern Sie, wie Sie die vom Infrastrukturteam angegebenen Probleme angesprochen haben.

### Lösung für fehlgeschlagene Bereitstellung {#solution-deployment-failed}

Überprüfen Sie die Bereitstellungsprotokolle:

* [Protokolle anzeigen und verwalten](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations) in unserem Commerce on Cloud Infrastructure Guide.
* [Überprüfen des Bereitstellungsprotokolls, wenn die Cloud-Benutzeroberfläche *`log snipped`* error](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error) in unserer Commerce-Wissensdatenbank.

1. Wenn die Bereitstellung während der `setup:upgrade` Schritt, die [!DNL cron] wurde nicht erneut aktiviert.
Beispiel: Sie sehen diese Zeile im Bereitstellungsprotokoll:

   ```The command "/bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade --keep-generated --ansi --no-interaction  | tee -a /app/$<project_id>/var/log/install_upgrade.log"" failed. Cache types config flushed successfully```

1. Andernfalls kann die Bereitstellung während einer anderen Phase fehlgeschlagen sein. Überprüfen Sie das Bereitstellungsprotokoll und stellen Sie sicher, dass beide Zeilen angezeigt werden (Beispiel unten). Wenn Sie nicht beide Zeilen sehen, die diesem im Protokoll ähnlich sind, bedeutet dies, dass die [!DNL cron] wurde nicht erneut aktiviert:

   ```  [2024-03-06T10:55:39.345564+00:00] INFO: Disable cron```<br>
...<br>
   ```  [2024-02-07T10:50:09.579005+00:00] INFO: Enable cron```

**Senden einer [Support-Anfrage](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) wenn Sie weitere Hilfe benötigen.**
