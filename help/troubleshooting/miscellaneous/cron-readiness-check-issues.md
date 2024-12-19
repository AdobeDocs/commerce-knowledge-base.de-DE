---
title: Probleme mit der Cron-Bereitschaftsprüfung
description: 'Dieser Artikel bietet Lösungen für Probleme mit der Cron-Bereitschaft. Im Folgenden finden Sie Symptome von Cron-Problemen:'
exl-id: 1f2cee2c-98ad-4cf5-af16-d736fced2a15
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Probleme mit der Cron-Bereitschaftsprüfung

Dieser Artikel bietet Lösungen für Probleme mit der Cron-Bereitschaft. Im Folgenden finden Sie Symptome von Cron-Problemen:

* Eine Fehlermeldung über die PHP-Einstellung `$HTTP_RAW_POST_DATA` wird angezeigt, obwohl sie richtig eingestellt ist.
* Die PHP Readiness Check zeigt die PHP-Version nicht an, wie die folgende Abbildung zeigt:
  ![upgr-tshooting-no-cron.png](assets/upgr-tshoot-no-cron.png)
* Der folgende Fehler wird in Commerce Admin angezeigt:
  ![compman-cron-not-running.png](assets/compman-cron-not-running.png)
Um den Fehler anzuzeigen, müssen Sie möglicherweise wie folgt **Systemmeldungen** oben im Fenster klicken:
  ![compman_sys-messages.png](assets/compman_sys-messages.png)

## Überprüfen der vorhandenen crontab {#check-your-existing-crontab}

In diesem Abschnitt wird beschrieben, wie Sie sehen, ob Cron derzeit ausgeführt wird, und überprüfen, ob es ordnungsgemäß eingerichtet ist.

So überprüfen Sie, ob Ihr crontab eingerichtet ist:

1. Melden Sie sich bei Ihrem Commerce-Server als Besitzer des [Magento-Dateisystems an oder wechseln Sie zu diesem](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/file-system/overview).
1. Überprüfen Sie, ob die folgende Datei vorhanden ist: `$ ls -al <magento_root>/var/.setup_cronjob_status`. Wenn die Datei vorhanden ist, wurde Cron in der Vergangenheit erfolgreich ausgeführt. Wenn die Datei *nicht* vorhanden ist, haben Sie Adobe Commerce noch nicht installiert oder Cron wird nicht ausgeführt. Fahren Sie in beiden Fällen mit dem nächsten Schritt fort.
1. Erhalten Sie weitere Details zu Cron. Geben Sie als Benutzer mit `root` Berechtigungen den folgenden Befehl ein: `$ crontab -u <Magento file system owner name> -l`. Zum Beispiel auf CentOS-`$ crontab -u magento_user -l`. Wenn für den Benutzer keine crontab eingerichtet wurde, wird die folgende Meldung angezeigt:    `no crontab for magento_user`. Ihr crontab sagt Ihnen Folgendes:
   * Welche PHP-Binärdatei Sie verwenden (in einigen Fällen haben Sie mehr als eine)
   * Welche Adobe Commerce Cron-Skripte Sie ausführen (insbesondere die Pfade zu diesen Skripten)
   * Wo sich Ihre Cron-Protokolle befinden

   Eine Lösung für Ihr Problem finden Sie in einem der folgenden Abschnitte.

## Lösung: crontab nicht eingerichtet {#solution-crontab-not-set-up}

Um sicherzustellen, dass Ihre Cron-Aufträge ordnungsgemäß eingerichtet sind, lesen Sie [Einrichten von Cron-Aufträgen](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/next-steps/configuration) in unserer Entwicklerdokumentation.

## Lösung: Cron läuft von falscher PHP-Binärdatei {#solution-cron-running-from-incorrect-php-binary}

Wenn Ihr Cron-Job eine andere PHP-Binärdatei als das Webserver-Plug-in verwendet, können PHP-Einstellungsfehler angezeigt werden. Um das Problem zu beheben, stellen Sie identische PHP-Einstellungen sowohl für die PHP-Befehlszeile als auch für das PHP-Webserver-Plug-in ein.

Weitere Informationen zu PHP-Einstellungen finden Sie unter [Erforderliche PHP-Einstellungen](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings) in unserer Entwicklerdokumentation.

## Lösung: Cron mit Fehlern läuft {#solution-cron-running-with-errors}

Führen Sie die einzelnen Befehle manuell aus, da der Befehl möglicherweise hilfreiche Fehlermeldungen anzeigt. Siehe [Einrichten von Cron-Aufträgen](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/next-steps/configuration) in unserer Entwicklerdokumentation.

>[!NOTE]
>
>Sie müssen cron mindestens *zweimal* ausführen, damit der Auftrag ausgeführt wird. Beim ersten Mal werden Aufträge in die Warteschlange gestellt, beim zweiten Mal werden die Aufträge ausgeführt.
