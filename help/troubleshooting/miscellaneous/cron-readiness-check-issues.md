---
title: Probleme bei der Cron-Bereitschaft-Überprüfung
description: '"Dieser Artikel bietet Lösungen für Probleme mit der Cron-Bereitschaft. Die folgenden Symptome treten bei Cron-Problemen auf:'''
exl-id: 1f2cee2c-98ad-4cf5-af16-d736fced2a15
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Probleme bei der Cron-Bereitschaft-Überprüfung

Dieser Artikel bietet Lösungen für Probleme mit der Cron-Bereitschaft. Im Folgenden finden Sie Symptome von Cron-Problemen:

* Eine Fehlermeldung über die PHP-Einstellung &quot;`$HTTP_RAW_POST_DATA`&quot; wird angezeigt, obwohl sie richtig eingestellt ist.
* Die PHP Ready Check zeigt die PHP-Version nicht wie in der folgenden Abbildung dargestellt an:
  ![upgr-tshooting-no-cron.png](assets/upgr-tshoot-no-cron.png)
* Der folgende Fehler wird in Commerce Admin angezeigt:
  ![compman-cron-not-running.png](assets/compman-cron-not-running.png)
Um den Fehler anzuzeigen, müssen Sie möglicherweise oben im Fenster auf **Systemmeldungen** klicken:
  ![compman_sys-messages.png](assets/compman_sys-messages.png)

## Überprüfen Sie die vorhandene Registerkarte {#check-your-existing-crontab}

In diesem Abschnitt wird beschrieben, wie Sie sehen, ob Cron derzeit ausgeführt wird, und überprüfen, ob es ordnungsgemäß eingerichtet ist.

So überprüfen Sie, ob Ihr Crontab eingerichtet ist:

1. Melden Sie sich bei Ihrem Commerce-Server als [Magento-Dateisysteminhaber](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/file-system/overview) an oder wechseln Sie zu ihm.
1. Überprüfen Sie, ob die folgende Datei vorhanden ist: `$ ls -al <magento_root>/var/.setup_cronjob_status`. Wenn die Datei vorhanden ist, hat cron in der Vergangenheit erfolgreich ausgeführt. Wenn die Datei *nicht* vorhanden ist, haben Sie Adobe Commerce noch nicht installiert oder Cron wird nicht ausgeführt. Fahren Sie in beiden Fällen mit dem nächsten Schritt fort.
1. Erfahren Sie mehr über Cron. Geben Sie als Benutzer mit `root` -Berechtigungen den folgenden Befehl ein: `$ crontab -u <Magento file system owner name> -l`. Beispiel: bei CentOS `$ crontab -u magento_user -l`. Wenn für den Benutzer kein Crontab eingerichtet wurde, wird die folgende Meldung angezeigt:    `no crontab for magento_user`. Ihr Crontab sagt Ihnen Folgendes:
   * Welche PHP-Binärdatei Sie verwenden (in einigen Fällen haben Sie mehr als eine)
   * Welche Adobe Commerce-Cron-Skripte Sie ausführen (insbesondere die Pfade zu diesen Skripten)
   * Wo sich Ihre Cron-Protokolle befinden

   In einem der folgenden Abschnitte finden Sie eine Lösung für Ihr Problem.

## Lösung: crontab nicht eingerichtet {#solution-crontab-not-set-up}

Um sicherzustellen, dass Ihre Cron-Aufträge ordnungsgemäß eingerichtet sind, lesen Sie [Einrichten von Cron-Aufträgen](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/next-steps/configuration) in unserer Entwicklerdokumentation.

## Lösung: cron läuft aus falscher PHP-Binärdatei {#solution-cron-running-from-incorrect-php-binary}

Wenn Ihr Cron-Job eine PHP-Binärdatei verwendet, die sich vom Webserver-Plug-in unterscheidet, werden möglicherweise Fehler bezüglich PHP-Einstellungen angezeigt. Um das Problem zu beheben, legen Sie identische PHP-Einstellungen für die PHP-Befehlszeile und das PHP-Webserver-Plug-in fest.

Weitere Informationen zu PHP-Einstellungen finden Sie unter [Erforderliche PHP-Einstellungen](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings) in unserer Entwicklerdokumentation.

## Lösung: cron läuft mit Fehlern {#solution-cron-running-with-errors}

Versuchen Sie, jeden Befehl manuell auszuführen, da der Befehl möglicherweise hilfreiche Fehlermeldungen anzeigt. Siehe [Einrichten von Cron-Aufträgen](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/next-steps/configuration) in unserer Entwicklerdokumentation.

>[!NOTE]
>
>Sie müssen cron mindestens *zweimal* ausführen, damit der Auftrag ausgeführt wird. Das erste Mal, dass Aufträge in die Warteschlange gestellt werden, das zweite Mal, um die Aufträge auszuführen.
