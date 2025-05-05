---
title: Überprüfen, warum  [!DNL cron]  deaktiviert wurde
description: Dieser Artikel bietet Lösungen zur Fehlerbehebung bei Problemen mit Cron in Adobe Commerce bei Cloud-Infrastrukturprodukten.
feature: Configuration
role: Developer
exl-id: d4d4a28d-3afa-4379-afc1-bc6250717784
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Überprüfen, warum [!DNL cron] deaktiviert wurde

Dieser Artikel bietet Lösungen zur Fehlerbehebung bei Problemen mit [!DNL cron] in Adobe Commerce mit Cloud-Infrastrukturprodukten.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle Versionen

## Problem

## Im Folgenden finden Sie Symptome für [!DNL cron] Probleme:

Sie haben bemerkt, dass Ihr [!DNL cron] nicht läuft.
Beispiel: In der `app/etc/env.php`-Datei werden die folgenden Zeilen angezeigt:

```'cron' =>
  array (
    'enabled' => 0
  ),
```

Ein leeres Array würde bedeuten, dass die [!DNL cron] **aktiviert**:

```'cron' =>
  array (
  ),
```

## Ursachen

Es gibt mehrere Gründe, warum die [!DNL cron] derzeit nicht aktiv ist:

1. Der [!DNL cron] wurde aufgrund verpasster [!DNL OpCache] deaktiviert.
1. Das Infrastruktur-Team hat Ihre [!DNL cron] deaktiviert, da dies dazu geführt hat, dass Ihre Site schlecht funktioniert bzw. heruntergefahren wurde.
1. Die [!DNL cron] wurde nicht erneut aktiviert, da die Bereitstellung fehlgeschlagen ist.

Eine Lösung für Ihr Problem finden Sie in einem der folgenden Abschnitte.

## Lösungen

### Lösung für [!DNL OpCache] {#solution-missed-opcache-settings}

Siehe [[!DNL Cron] aufgrund falsch konfigurierter oder fehlender Einstellungen [!DNL OpCache]  in ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/crons-blocked-running-missing-opache-settings) Wissensdatenbank zu Commerce.

### Lösung für „Deaktiviert“ durch Infrastrukturteam {#solution-disabled-by-infrastructure-team}

1. Überprüfen Sie Ihre vorherigen Support-Tickets, bei denen Ihre Site nicht verfügbar war oder nicht reagierte.
1. Überprüfen Sie dann, ob das Infrastruktur-Team angegeben hat, dass es deaktiviert wurde.
1. Vergewissern Sie sich, dass Sie die vom Infrastruktur-Team angesprochenen Probleme/Bedenken berücksichtigt haben.
1. Senden Sie eine [Support-Anfrage](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets), wenn Sie weitere Hilfe benötigen, um die [!DNL cron] wieder zu aktivieren, und erklären Sie, wie Sie die vom Infrastruktur-Team angegebenen Probleme behoben haben.

### Lösung für Bereitstellung fehlgeschlagen {#solution-deployment-failed}

Überprüfen Sie die Bereitstellungsprotokolle:

* [Anzeigen und Verwalten von Protokollen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/test/log-locations) finden Sie in unserem Handbuch zu Commerce in Cloud-Infrastrukturen .
* [Überprüfen des Bereitstellungsprotokolls, ob die Cloud](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error)Benutzeroberfläche einen *`log snipped`* Fehler aufweist, in unserer Commerce-Wissensdatenbank.

1. Wenn die Bereitstellung während des `setup:upgrade` fehlgeschlagen wäre, wurde die [!DNL cron] nicht erneut aktiviert.
Beispiel: Diese Zeile wird im Bereitstellungsprotokoll angezeigt:

   ```The command "/bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade --keep-generated --ansi --no-interaction  | tee -a /app/$<project_id>/var/log/install_upgrade.log"" failed. Cache types config flushed successfully```

1. Andernfalls ist die Bereitstellung möglicherweise in einem anderen Schritt fehlgeschlagen. Überprüfen Sie das Bereitstellungsprotokoll und stellen Sie sicher, dass beide Zeilen angezeigt werden (Beispiel unten). Wenn nicht beide ähnlichen Zeilen im Protokoll angezeigt werden, bedeutet dies, dass die [!DNL cron] nicht erneut aktiviert wurde:

   ```  [2024-03-06T10:55:39.345564+00:00] INFO: Disable cron```<br>
…<br>
   ```  [2024-02-07T10:50:09.579005+00:00] INFO: Enable cron```

**Senden Sie eine [Support-Anfrage](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets), wenn Sie weitere Hilfe benötigen.**
