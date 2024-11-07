---
title: Zurücksetzen der Umgebung auf Adobe Commerce in der Cloud-Infrastruktur
description: In diesem Artikel werden verschiedene Szenarien für die Zurücksetzung einer Umgebung in Adobe Commerce in der Cloud-Infrastruktur vorgestellt.
exl-id: e6b27838-ca1e-415f-a098-2aa2576e3f20
feature: Best Practices, Build, Cloud, Console
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '1093'
ht-degree: 0%

---

# Zurücksetzen der Umgebung auf Adobe Commerce in der Cloud-Infrastruktur

In diesem Artikel werden verschiedene Szenarien für die Zurücksetzung einer Umgebung in Adobe Commerce in der Cloud-Infrastruktur vorgestellt.

Wählen Sie die für Ihren Fall am besten geeignete Option aus:

* Wenn Sie die Aktivität (geplante Bereitstellung oder Aktualisierung) - [Szenario 1: Geplante Aktivität)](#scen1) geplant haben.
* Wenn Sie einen gültigen Snapshot haben - [Szenario 2: Snapshot wiederherstellen](#scen2).
* Wenn Sie einen stabilen Build haben, aber keine gültige Momentaufnahme - [Szenario 3: Kein Snapshot, Build Stable (SSH-Verbindung verfügbar)](#scen3).
* Wenn der Build beschädigt ist und Sie keinen gültigen Snapshot haben - [Szenario 4: Kein Snapshot; Build defekt (keine SSH-Verbindung)](#scen4).

## Szenario 1: Geplante Aktivität

Bei einer geplanten Bereitstellung oder Aktualisierung wäre der Händler am einfachsten und empfohlener [!UICONTROL Rollback], als Teil Ihrer Vorbereitungen Folgendes zu tun:

>[!NOTE]
>
>Testen Sie diese Schritte immer zuerst in Ihrem **[!UICONTROL Staging Environment]**!

<u>Fünf Tage vor der Upgrade-/Bereitstellungsaktivität</u>:

1. Überprüfen Sie die Größe der aktuellen Datenbank.
1. Vergewissern Sie sich, dass Sie genügend Speicherplatz auf `/data/exports` haben, um eine [!UICONTROL Database Dump] aufzunehmen. Wenn Sie nicht genügend Festplattenspeicher haben, entfernen Sie entweder unerwünschte Daten oder erstellen Sie einen Support-Fall und fordern Sie die Erweiterung der Festplatte an.

<u>Am Tag der Änderungen</u>:

1. Platzieren Sie die Website in [!UICONTROL Maintenance Mode].
Weitere Informationen zu [Aktivieren oder Deaktivieren von [!UICONTROL Maintenance Mode]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html) finden Sie in unserem Benutzerhandbuch und den [[!UICONTROL Maintenance Mode] Optionen für die Aktualisierung](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/troubleshooting/maintenance-mode-options.html) in unserem Upgrade-Handbuch.
1. Deaktivieren Sie Cron-Aufträge. Weitere Informationen zum Deaktivieren von Cron-Aufträgen finden Sie in unserem [Eigenschaftsleitfaden für Crons](<https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property#disable-cron-jobs>).
1. Nehmen Sie eine lokale [[!UICONTROL Database Dump]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/create-database-dump-on-cloud.html).

<u>Wenn ein [!UICONTROL Rollback] erforderlich ist</u>:

1. Wenn Anwendungen wie [!DNL MariaDB] im Rahmen dieser geplanten Aktivität aktualisiert wurden, lassen Sie diese Anwendung zuerst auf eine frühere Version neu installieren.
1. [!UICONTROL Rollback] die Datenbank mit der lokalen [!UICONTROL Database Dump] und importieren Sie diese zurück in [!DNL MariaDB].
1. [!UICONTROL Rollback] den Code über [!DNL Git] zu einer vorherigen funktionierenden Version.

Die Verwendung von [!UICONTROL Snapshots] ist nicht die empfohlene Methode für die Aktualisierung/geplante Aktivität [!UICONTROL rollbacks/restores], da es viel länger dauert, die Daten im Vergleich zu einer lokalen [!UICONTROL Database Dump] abzurufen, wie oben in Schritt 2 des Abschnitts **Wenn ein [!UICONTROL Rollback] erforderlich ist** beschrieben.

[!UICONTROL Snapshots] wird nicht auf dem Knoten/Server gespeichert, sondern in einem separaten Speicherblock gespeichert. Da diese Daten vom Blockspeicher über das Netzwerk auf eine neue Festplatte übertragen werden müssen, dauert es im Prozess Zeit. Diese neue Festplatte wird dann auf den Knoten gemountet, der zum Abrufen/Import auf die ursprüngliche Festplatte bereit ist, die mit dem Knoten/Server verbunden ist.

Wenn Sie dies mit dem Import eines lokalen [!UICONTROL Database Dump] vergleichen, können die Daten bereits auf dem Knoten/Server abgerufen werden, sodass viel Zeit gespeichert wird, da nur ein [!UICONTROL Database Import] erforderlich ist.

## Szenario 2: Momentaufnahme wiederherstellen

Lesen Sie: [Wiederherstellen einer Momentaufnahme auf Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-snapshot) in unserer Entwicklerdokumentation.

>[!NOTE]
>
>Die Erstellung eines Schnappschusses muss unser erster Schritt nach dem Zugriff auf Adobe Commerce über das Cloud-Infrastrukturkonto und vor der Anwendung größerer Änderungen sein. Dies ist eine Best Practice und wird dringend empfohlen.

Lesen Sie: [Erstellen Sie eine Momentaufnahme](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#create-snapshot) in unserer Entwicklerdokumentation.

## Szenario 3: Keine Momentaufnahme, Build-Stable (SSH-Verbindung verfügbar)

In diesem Abschnitt wird gezeigt, wie Sie eine Umgebung zurücksetzen, wenn Sie keine Momentaufnahme erstellt haben, aber über SSH auf die Umgebung zugreifen können.

Die Schritte sind:

1. Deaktivieren Sie die Konfigurationsverwaltung.
1. Deinstallieren Sie die Adobe Commerce-Software.
1. Setzen Sie den Zweig [!DNL git] zurück.

Führen Sie diese Schritte aus:

* Ihre Adobe Commerce-Installation kehrt zum Vanilla-Status zurück (Datenbank wiederhergestellt, Bereitstellungskonfiguration entfernt, Ordner unter `var` gelöscht).
* Ihr [!DNL git] -Zweig wird in der Vergangenheit auf den gewünschten Status zurückgesetzt.

Lesen Sie die detaillierten Schritte unten.

### Schritt 0 (Voraussetzung): Entfernen Sie config.php, um die Konfigurationsverwaltung zu deaktivieren

Wir müssen Configuration Management deaktivieren, damit die vorherigen Konfigurationseinstellungen während der Bereitstellung nicht automatisch angewendet werden.

Um Configuration Management zu deaktivieren, stellen Sie sicher, dass Ihr `/app/etc/` -Verzeichnis nicht die Datei `config.php` enthält.

Gehen Sie wie folgt vor, um die Konfigurationsdatei zu entfernen:

1. [SSH in Ihre Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Entfernen Sie die Konfigurationsdatei: `rm app/etc/config.php`

Weitere Informationen zur Konfigurationsverwaltung:

* [Reduzieren Sie die Ausfallzeiten bei der Bereitstellung auf Adobe Commerce in der Cloud-Infrastruktur](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) in unserer Support-Wissensdatenbank.
* [Konfigurationsverwaltung für Speichereinstellungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) in unserer Entwicklerdokumentation.

### Schritt 1: Deinstallieren Sie die Adobe Commerce-Software mit setup:uninstall-Befehl


Durch die Deinstallation der Adobe Commerce-Software wird die Datenbank gelöscht, die Bereitstellungskonfiguration entfernt und die Ordner unter `var` gelöscht.

Lesen Sie: [Deinstallieren Sie die Adobe Commerce-Software](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html) in unserer Entwicklerdokumentation.

Gehen Sie wie folgt vor, um die Adobe Commerce-Software zu deinstallieren:

1. [SSH in Ihre Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Ausführen von `setup:uninstall` : `bin/magento setup:uninstall`
1. Bestätigen Sie die Deinstallation.

Die folgende Meldung wird angezeigt, um eine erfolgreiche Deinstallation zu bestätigen:

```php
[SUCCESS]: Magento uninstallation complete.
```

Dies bedeutet, dass wir unsere Adobe Commerce-Installation (einschließlich DB) wieder in ihren authentischen Zustand (Vanilla) zurückversetzt haben.

### Schritt 2: Zurücksetzen des Zweigs [!DNL git]

Beim Zurücksetzen von [!DNL git] wird der Code in der Vergangenheit wieder in den gewünschten Status zurückgesetzt.

1. Klonen Sie die Umgebung in Ihre lokale Entwicklungsumgebung. Sie können den Befehl in die Cloud-Konsole kopieren:    ![copy_git_clone.png](assets/copy_git_clone.png)
1. Rufen Sie den Commits-Verlauf auf. Verwenden Sie `--reverse`, um den Verlauf für mehr Komfort in umgekehrter Reihenfolge anzuzeigen: `git log --reverse`
1. Wählen Sie den Commit-Hash aus, für den Sie gut waren. Um den Code auf seinen authentischen Status (Vanilla) zurückzusetzen, suchen Sie den allerersten Commit, der Ihre Verzweigung (Umgebung) erstellt hat.
   ![alt text](image.png)
1. Anwenden von Hard [!DNL git] reset: `git reset --h <commit_hash>`
1. Push-Änderungen an Server: `git push --force <origin> <branch>`

Nachdem Sie diese Schritte ausgeführt haben, wird der [!DNL git]-Zweig zurückgesetzt und der gesamte [!DNL git]-Änderungsprotokoll ist klar. Die letzten [!DNL git] Push-Trigger führen die Bereitstellung erneut durch, um alle Änderungen anzuwenden und Adobe Commerce erneut zu installieren.

## Szenario 4: Kein Schnappschuss; beschädigter Build (keine [!DNL SSH] Verbindung)

In diesem Abschnitt wird gezeigt, wie eine Umgebung zurückgesetzt wird, wenn sie sich in einem kritischen Zustand befindet: Das Implementierungsverfahren kann beim Erstellen einer funktionierenden Anwendung nicht erfolgreich sein, sodass die [!DNL SSH]-Verbindung nicht verfügbar ist.

In diesem Szenario müssen Sie zunächst den Arbeitsstatus Ihrer Adobe Commerce-Anwendung mithilfe von [!DNL git] zurücksetzen und dann die Adobe Commerce-Software deinstallieren (um die Datenbank abzulegen und wiederherzustellen, die Bereitstellungskonfiguration zu entfernen usw.). Das Szenario umfasst dieselben Schritte wie in Szenario 3, aber die Reihenfolge der Schritte ist anders und es gibt einen zusätzlichen Schritt - &quot;Erzwingen der erneuten Bereitstellung&quot;. Die Schritte sind:

1. [Setzen Sie den Zweig [!DNL git] zurück.](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)
1. [Deaktivieren Sie die Konfigurationsverwaltung.](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)
1. [Deinstallieren Sie die Adobe Commerce-Software.](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)
1. Erzwingen Sie die erneute Bereitstellung.

Nachdem Sie diese Schritte ausgeführt haben, haben Sie dieselben Ergebnisse wie in Szenario 3.

### Schritt 4: Erzwingen der erneuten Bereitstellung

Erstellen Sie einen Commit (dies kann ein leerer Commit sein, obwohl wir ihn nicht empfehlen) und pushen Sie ihn auf den Server, um eine erneute Bereitstellung des Triggers durchzuführen:

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## Wenn Setup:uninstall fehlschlägt, die Datenbank manuell zurücksetzen

Wenn die Ausführung des Befehls `setup:uninstall` mit einem Fehler fehlschlägt und nicht abgeschlossen werden kann, können wir die DB mit den folgenden Schritten manuell löschen:

1. [SSH in Ihre Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Stellen Sie eine Verbindung zur MySQL DB her: `mysql -h database.internal` (Informationen zu Pro-Umgebungen finden Sie unter: [MySQL-Dienst einrichten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html)).
1. Legen Sie die `main` DB ab: `drop database main;`
1. Erstellen Sie eine leere `main` DB: `create database main;`
1. Löschen Sie die folgenden Konfigurationsdateien: `config.php`, `config.php.bak`, `env.php`, `env.php.bak`

Nachdem Sie die DB zurückgesetzt haben, senden [Sie einen  [!DNL git] Push in die Umgebung, um den Trigger erneut bereitzustellen](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli.html) und installieren Sie Adobe Commerce in einer neu erstellten DB. Oder [führen Sie den Befehl zum erneuten Bereitstellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#environment-commands) aus.
