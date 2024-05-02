---
title: Fehlerbehebung bei Cron
description: In diesem Artikel finden Sie Lösungen zur Fehlerbehebung bei Problemen mit Cron in Adobe Commerce vor Ort.
exl-id: e69a4fb3-731b-449e-a815-c33cd2faa567
feature: Configuration
role: Developer
source-git-commit: b6a79bcff3d757d40e7070182d8853a37960a782
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Fehlerbehebung bei Cron

In diesem Artikel finden Sie Lösungen zur Fehlerbehebung bei Problemen mit Cron in Adobe Commerce vor Ort.

## Betroffene Produkte und Versionen

* Adobe Commerce lokal 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Probleme

## Im Folgenden finden Sie Symptome von Cron-Problemen:

* Ihre Aktualisierung oder Aktualisierung wird nie ausgeführt. Sie bleibt in einem `pending` state.
* Eine Fehlermeldung zur [PHP](https://glossary.magento.com/php) Einstellung `$HTTP_RAW_POST_DATA` angezeigt, obwohl sie richtig eingestellt ist.
* Die Prüfung der Cron-Bereitschaft schlägt fehl. Mögliche Fehler sind nicht beschreibbare Pfade und nicht eingerichtetes Cron. Ein Beispiel:

  ![upgr-tshooting-no-cron2.png](assets/upgr-tshoot-no-cron2.png)

* Die PHP Ready Check zeigt die PHP-Version nicht wie in der folgenden Abbildung dargestellt.

  ![screen_shot_2019-08-29_at_1.36.08_PM.png](assets/Screen_Shot_2019-08-29_at_1.36.08_PM.png)

* Der folgende Fehler wird in Commerce Admin angezeigt:

  ![compman-cron-not-running.png](assets/compman-cron-not-running.png)

Um den Fehler anzuzeigen, müssen Sie möglicherweise auf **Systemmeldungen** oben im Fenster wie folgt:

![compman_sys-messages.png](assets/compman_sys-messages.png)

## Untersuchen, um die Ursache zu finden {#check-your-existing-crontab}

In diesem Abschnitt wird beschrieben, wie Sie sehen, ob Cron derzeit ausgeführt wird, und überprüfen, ob es ordnungsgemäß eingerichtet ist.

Gehen Sie wie folgt vor, um zu überprüfen, ob die Registerkarte &quot;Crontab&quot;eingerichtet ist:

1. Melden Sie sich bei Ihrem Magento-Server an oder wechseln Sie zu dem [Magento-Dateisysteminhaber](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html).
1. Überprüfen Sie, ob die folgende Datei vorhanden ist:    `bash    ls -al <magento_root>/var/.setup_cronjob_status`. Wenn die Datei vorhanden ist, hat cron in der Vergangenheit erfolgreich ausgeführt. Wenn die Datei *nicht* vorhanden sind, entweder haben Sie noch keine Magento installiert oder Cron läuft nicht. Fahren Sie in beiden Fällen mit dem nächsten Schritt fort.
1. Erfahren Sie mehr über Cron. Als Benutzer mit `root` -Berechtigungen verwenden, geben Sie den folgenden Befehl ein:    `bash    crontab -u <Magento file system owner name> -l`. Beispiel: unter CentOS `bash    crontab -u magento_user -l`.  Wenn für den Benutzer kein Crontab eingerichtet wurde, wird die folgende Meldung angezeigt:    `terminal    no crontab for magento_user`. Ihr Crontab sagt Ihnen Folgendes:

   * Welche PHP-Binärdatei Sie verwenden (in einigen Fällen haben Sie mehr als eine)
   * Welche Magento-Cron-Skripte Sie ausführen (insbesondere die Pfade zu diesen Skripten)
   * Wo sich Ihre Cron-Protokolle befinden

In einem der folgenden Abschnitte finden Sie eine Lösung für Ihr Problem.

## Lösungen

### Lösung für Crontab nicht eingerichtet {#solution-crontab-not-set-up}

Informationen zum Überprüfen der ordnungsgemäßen Einrichtung Ihrer Cron-Aufträge finden Sie unter [Einrichten von Cron-Aufträgen](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron).

### Lösung für Cron, das aus einer falschen PHP-Binärdatei läuft {#solution-cron-running-from-incorrect-php-binary}

Wenn Ihr Cron-Job eine PHP-Binärdatei verwendet, die sich vom Webserver-Plug-in unterscheidet, werden möglicherweise Fehler bezüglich PHP-Einstellungen angezeigt. Um das Problem zu beheben, legen Sie identische PHP-Einstellungen für die PHP-Befehlszeile und das PHP-Webserver-Plug-in fest.

Weitere Informationen zu PHP-Einstellungen finden Sie unter [Erforderliche PHP-Einstellungen](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html) in unserer Entwicklerdokumentation.

### Lösung für Cron, das mit Fehlern läuft {#solution-cron-running-with-errors}

Versuchen Sie, jeden Befehl manuell auszuführen, da der Befehl möglicherweise hilfreiche Fehlermeldungen anzeigt. Siehe [Einrichten von Cron-Aufträgen](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron).

>[!NOTE]
>
>Sie müssen cron mindestens ausführen *zweimal* für den Auftrag, der ausgeführt werden soll; das erste Mal, dass Aufträge in die Warteschlange gestellt werden, das zweite Mal, dass die Aufträge ausgeführt werden.
