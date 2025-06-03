---
title: Umgebung auf Adobe Commerce auf Cloud-Infrastruktur zurücksetzen
description: Dieser Artikel zeigt verschiedene Szenarien für das Zurücksetzen einer Umgebung auf Adobe Commerce in der Cloud-Infrastruktur.
exl-id: e6b27838-ca1e-415f-a098-2aa2576e3f20
feature: Best Practices, Build, Cloud, Console
source-git-commit: 4327f464fb8eebf30a380e9e58afe55c3e613e52
workflow-type: tm+mt
source-wordcount: '1110'
ht-degree: 0%

---

# Umgebung auf Adobe Commerce auf Cloud-Infrastruktur zurücksetzen

Dieser Artikel zeigt verschiedene Szenarien für das Zurücksetzen einer Umgebung auf Adobe Commerce in der Cloud-Infrastruktur.
>[!NOTE]
>
>Dieses Handbuch gilt für alle Cloud Starter-Umgebungen und nur für Integrationsumgebungen in Cloud Pro.

Wählen Sie das für Ihren Fall am besten geeignete aus:

* Wenn Sie eine geplante Aktivität (geplante Bereitstellung oder Aktualisierung) haben - [Szenario 1: Geplante Aktivität)](#scen1).
* Wenn Sie einen gültigen Schnappschuss haben - [Szenario 2: Wiederherstellen eines Schnappschusses](#scen2).
* Wenn Sie einen stabilen Build, aber keinen gültigen Snapshot haben - ([ 3: Kein Snapshot, Build stabil (SSH-Verbindung verfügbar)](#scen3).
* Wenn der Build beschädigt ist und Sie keinen gültigen Snapshot haben - [Szenario 4: Kein Snapshot; Build beschädigt (keine SSH-Verbindung)](#scen4).

## Szenario 1: Geplante Aktivität

Bei einer geplanten Bereitstellung oder Aktualisierung wäre die einfachste und empfohlene [!UICONTROL Rollback], dass der Händler im Rahmen Ihrer Vorbereitungen die folgenden Schritte durchführt:

>[!NOTE]
>
>Testen Sie diese Schritte immer zuerst in Ihrer unteren Umgebung!

<u>Fünf Tage vor der Aktualisierung/Bereitstellung</u>:

1. Überprüfen Sie die Größe der aktuellen Datenbank.
1. Vergewissern Sie sich, dass auf dem `/data/exports` genügend Speicherplatz für ein [!UICONTROL Database Dump] vorhanden ist. Wenn Sie nicht über genügend Speicherplatz verfügen, entfernen Sie unerwünschte Daten oder erstellen Sie einen Support-Fall und fordern Sie die Erweiterung der Festplatte an.

<u>Am Tag der Änderungen</u>:

1. Platzieren Sie die Website in [!UICONTROL Maintenance Mode].
Lesen Sie mehr über [Aktivieren oder Deaktivieren von [!UICONTROL Maintenance Mode]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html?lang=de) in unserem Benutzerhandbuch und [[!UICONTROL Maintenance Mode] Upgrade-Optionen](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/troubleshooting/maintenance-mode-options.html?lang=de) in unserem Upgrade-Handbuch.
1. Deaktivieren Sie Cron-Aufträge. Weitere Informationen zum Deaktivieren von Cron-Aufträgen finden Sie in unserem [crons properties guide](<https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property#disable-cron-jobs>).
1. Nehmen Sie eine lokale [[!UICONTROL Database Dump]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/create-database-dump-on-cloud.html?lang=de).

<u>Wenn eine [!UICONTROL Rollback] erforderlich ist</u>:

1. Wenn Programme wie [!DNL MariaDB] im Rahmen dieser geplanten Aktivität aktualisiert wurden, muss diese Anwendung zuerst auf eine frühere Version neu installiert werden.
1. [!UICONTROL Rollback] Sie die Datenbank mithilfe der lokalen [!UICONTROL Database Dump] und importieren Sie sie wieder in [!DNL MariaDB].
1. [!UICONTROL Rollback] Sie den Code über [!DNL Git] auf eine frühere Arbeitsversion.

Die Verwendung von [!UICONTROL Snapshots] ist nicht die empfohlene Methode für die Aktualisierung/geplante [!UICONTROL rollbacks/restores], da es im Vergleich zu einer lokalen [!UICONTROL Database Dump] viel länger dauert, bis die Daten abgerufen werden, wie oben in Schritt 2 des **Wenn eine [!UICONTROL Rollback] erforderlich ist** Abschnitts beschrieben.

[!UICONTROL Snapshots] werden nicht auf dem Knoten/Server, sondern auf einem separaten Speicherblock gespeichert, und da diese Daten vom Blockspeicher über das Netzwerk auf eine neue Festplatte übertragen werden müssen, dauert es dabei lange. Diese neue Festplatte wird dann auf dem Knoten bereitgestellt, der abgerufen/importiert werden kann, und auf der ursprünglichen Festplatte, die mit dem Knoten/Server verbunden ist.

Wenn Sie dies mit dem Importieren einer lokalen [!UICONTROL Database Dump] vergleichen, können die Daten bereits auf dem Knoten/Server abgerufen werden, sodass viel Zeit gespart wird, da nur eine [!UICONTROL Database Import] erforderlich ist.

## Szenario 2: Wiederherstellen eines Snapshots

Lesen Sie [Wiederherstellen eines Snapshots auf Adobe Commerce in der Cloud](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-snapshot)Infrastruktur in unserer Entwicklerdokumentation.

>[!NOTE]
>
>Das Erstellen eines Snapshots muss unser erster Schritt sein, nachdem wir auf das Adobe Commerce on Cloud Infrastructure-Konto zugegriffen haben und bevor wir große Änderungen vornehmen. Dies ist eine Best Practice und wird dringend empfohlen.

Lesen Sie [Erstellen eines Schnappschusses](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#create-snapshot) in unserer Entwicklerdokumentation.

## Szenario 3: Kein Snapshot, Build stabil (SSH-Verbindung verfügbar)

Dieser Abschnitt zeigt, wie Sie eine Umgebung zurücksetzen, wenn Sie keinen Snapshot erstellt haben, aber über SSH auf die Umgebung zugreifen können.

Die Schritte sind:

1. Deaktivieren Sie die Konfigurationsverwaltung.
1. Deinstallieren Sie die Adobe Commerce-Software.
1. Setzen Sie die [!DNL git] zurück.

Nachdem Sie diese Schritte ausgeführt haben:

* Ihre Adobe Commerce-Installation kehrt in den Vanilla-Status zurück (Datenbank wiederhergestellt; Bereitstellungskonfiguration entfernt; Verzeichnisse unter `var` gelöscht).
* Ihre [!DNL git] Verzweigung wurde in der Vergangenheit auf den gewünschten Status zurückgesetzt.

Lesen Sie die detaillierten Schritte unten.

### Schritt 0 (Voraussetzung): Entfernen Sie config.php, um die Konfigurationsverwaltung zu deaktivieren

Wir müssen die Konfigurationsverwaltung deaktivieren, damit sie während der Bereitstellung nicht automatisch die vorherigen Konfigurationseinstellungen anwendet.

Um die Konfigurationsverwaltung zu deaktivieren, stellen Sie sicher, dass das `/app/etc/`-Verzeichnis nicht die `config.php` enthält.

Gehen Sie wie folgt vor, um die Konfigurationsdatei zu entfernen:

1. [SSH in Ihre Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=de).
1. Entfernen Sie die Konfigurationsdatei: `rm app/etc/config.php`

Weitere Informationen zur Konfigurationsverwaltung:

* [Verkürzen Sie Bereitstellungsausfälle auf Adobe Commerce auf Cloud](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md)Infrastrukturen in unserer Support-Wissensdatenbank.
* [Konfigurationsverwaltung für Store-Einstellungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=de) in unserer Entwicklerdokumentation.

### Schritt 1: Deinstallieren Sie die Adobe Commerce-Software mit dem Befehl setup:uninstall


Durch die Deinstallation der Adobe Commerce-Software wird die Datenbank gelöscht, die Bereitstellungskonfiguration entfernt und die Ordner unter `var` gelöscht.

Lesen Sie [Adobe Commerce-Software deinstallieren](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html?lang=de) in unserer Entwicklerdokumentation.

Gehen Sie wie folgt vor, um die Adobe Commerce-Software zu deinstallieren:

1. [SSH in Ihre Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=de).
1. `setup:uninstall` ausführen : `bin/magento setup:uninstall`
1. Deinstallation bestätigen.

Die folgende Meldung wird angezeigt, um eine erfolgreiche Deinstallation zu bestätigen:

```php
[SUCCESS]: Magento uninstallation complete.
```

Dies bedeutet, dass wir unsere Adobe Commerce-Installation (einschließlich DB) in ihren authentischen (Vanilla-)Status zurückgesetzt haben.

### Schritt 2: [!DNL git] zurücksetzen

Mit [!DNL git] Zurücksetzen kehren wir den Code in den gewünschten Status in der Vergangenheit zurück.

1. Klonen Sie die Umgebung in Ihre lokale Entwicklungsumgebung. Sie können den Befehl in die Cloud-Konsole kopieren:    ![copy_git_clone.png](assets/copy_git_clone.png)
1. Zugriff auf den Commit-Verlauf. `--reverse` verwenden, um den Verlauf in umgekehrter Reihenfolge anzuzeigen, um die Anzeige zu vereinfachen: `git log --reverse`
1. Wählen Sie den Commit-Hash aus, für den Sie gut waren. Um den Code in seinen authentischen Zustand (Vanilla) zurückzusetzen, suchen Sie den ersten Commit, mit dem Ihre Verzweigung (Umgebung) erstellt wurde.
   ![ALT-Text](image.png)
1. Anwenden des [!DNL git]-Zurücksetzungsprozesses: `git reset --h <commit_hash>`
1. Änderungen an Server pushen: `git push --force <origin> <branch>`

Nach dem Ausführen dieser Schritte wird unsere [!DNL git] zurückgesetzt und das gesamte [!DNL git]-Änderungsprotokoll ist gelöscht. Die letzten [!DNL git] pushen Trigger die erneute Bereitstellung, um alle Änderungen anzuwenden und Adobe Commerce neu zu installieren.

## Szenario 4: Kein Schnappschuss; Build beschädigt (keine [!DNL SSH])

In diesem Abschnitt wird gezeigt, wie eine Umgebung in einem kritischen Zustand zurückgesetzt wird: Das Bereitstellungsverfahren kann keine funktionierende Anwendung erstellen, sodass die [!DNL SSH] nicht verfügbar ist.

In diesem Szenario müssen Sie zunächst den Betriebsstatus Ihrer Adobe Commerce-Anwendung mithilfe [!DNL git] Zurücksetzen wiederherstellen und dann die Adobe Commerce-Software deinstallieren (um die Datenbank abzulegen und wiederherzustellen, die Bereitstellungskonfiguration zu entfernen usw.). Das Szenario umfasst dieselben Schritte wie in Szenario 3, aber die Reihenfolge der Schritte unterscheidet sich, und es gibt einen zusätzlichen Schritt: Erzwingen der erneuten Bereitstellung. Die Schritte sind:

1. [Setzen Sie die  [!DNL git]  zurück.](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)
1. [Deaktivieren Sie die Konfigurationsverwaltung.](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)
1. [Deinstallieren Sie die Adobe Commerce-Software.](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)
1. Erzwingen der erneuten Bereitstellung.

Nachdem Sie diese Schritte ausgeführt haben, erhalten Sie dieselben Ergebnisse wie in Szenario 3.

### Schritt 4: Erzwingen der erneuten Bereitstellung

Führen Sie einen Commit durch (dies kann ein leerer Commit sein, obwohl wir dies nicht empfehlen) und übertragen Sie ihn auf den -Server, um den Trigger erneut bereitzustellen:

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## Wenn setup:uninstall fehlschlägt, Datenbank manuell zurücksetzen

Wenn die Ausführung des `setup:uninstall`-Befehls mit einem Fehler fehlschlägt und nicht abgeschlossen werden kann, können wir die Datenbank mit diesen Schritten manuell löschen:

1. [SSH in Ihre Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=de).
1. Verbinden mit der MySQL-DB: `mysql -h database.internal` (Für Pro-Umgebungen siehe: [Einrichten des MySQL-](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html?lang=de)).
1. `main` DB ablegen: `drop database main;`
1. Leere `main`-DB erstellen: `create database main;`
1. Löschen Sie die folgenden Konfigurationsdateien: `config.php`, `config.php.bak`, `env.php`, `env.php.bak`

Nachdem Sie die DB zurückgesetzt haben[ führen Sie einen Push  [!DNL git]  die Umgebung aus, um den Trigger erneut bereitzustellen](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli.html?lang=de) und installieren Sie Adobe Commerce in einer neu erstellten DB. Oder [führen Sie den Befehl zum erneuten Bereitstellen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html?lang=de#environment-commands).
