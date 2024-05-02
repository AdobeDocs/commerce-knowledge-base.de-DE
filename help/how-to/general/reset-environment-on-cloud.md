---
title: Zurücksetzen der Umgebung auf Adobe Commerce in der Cloud-Infrastruktur
description: In diesem Artikel werden verschiedene Szenarien für die Zurücksetzung einer Umgebung in Adobe Commerce in der Cloud-Infrastruktur vorgestellt.
exl-id: e6b27838-ca1e-415f-a098-2aa2576e3f20
feature: Best Practices, Build, Cloud, Console
source-git-commit: ddde2385f1d94194b34e9ed51f6cbda55c916d90
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 0%

---

# Zurücksetzen der Umgebung auf Adobe Commerce in der Cloud-Infrastruktur

In diesem Artikel werden verschiedene Szenarien für die Zurücksetzung einer Umgebung in Adobe Commerce in der Cloud-Infrastruktur vorgestellt.

Wählen Sie die für Ihren Fall am besten geeignete Option aus:

* Wenn Sie eine Aktivität geplant haben (geplante Bereitstellung oder Aktualisierung) - [Szenario 1: Geplante Aktivität)](#scen1).
* Wenn Sie einen gültigen Schnappschuss haben: [Szenario 2: Momentaufnahme wiederherstellen](#scen2).
* Wenn Sie einen stabilen Build haben, aber keinen gültigen Schnappschuss - [Szenario 3: Keine Momentaufnahme, Build-Stable (SSH-Verbindung verfügbar)](#scen3).
* Wenn der Build beschädigt ist und Sie keinen gültigen Schnappschuss haben - [Szenario 4: Keine Momentaufnahme; Build defekt (keine SSH-Verbindung)](#scen4).

## Szenario 1: Geplante Aktivität

Mit einer geplanten Bereitstellung oder Aktualisierung ist die einfachste und empfohlene [!UICONTROL Rollback] wäre es Sache des Händlers, im Rahmen Ihrer Vorbereitungen Folgendes zu tun:

>[!NOTE]
>
>Testen Sie diese Schritte immer in Ihrem **[!UICONTROL Staging Environment]** first!

<u>Fünf Tage vor der Upgrade-/Bereitstellungsaktivität</u>:

1. Überprüfen Sie die Größe der aktuellen Datenbank.
1. Stellen Sie sicher, dass genügend Speicherplatz vorhanden ist. `/data/exports` um eine [!UICONTROL Database Dump]. Wenn Sie nicht genügend Festplattenspeicher haben, entfernen Sie entweder unerwünschte Daten oder erstellen Sie einen Support-Fall und fordern Sie die Erweiterung der Festplatte an.

<u>Am Tag der Änderungen</u>:

1. Platzieren Sie die Website in [!UICONTROL Maintenance Mode].<br>
Mehr dazu [Aktivieren oder Deaktivieren [!UICONTROL Maintenance Mode]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html) in unserem Benutzerhandbuch und [[!UICONTROL Maintenance Mode] Upgrade-Optionen](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/troubleshooting/maintenance-mode-options.html) in unserem Upgrade-Handbuch.
1. Nehmen Sie eine lokale [[!UICONTROL Database Dump]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/create-database-dump-on-cloud.html).

<u>Wenn eine [!UICONTROL Rollback] ist erforderlich</u>:

1. Wenn Anwendungen wie [!DNL MariaDB] im Rahmen dieser geplanten Aktivität aktualisiert wurde, lassen Sie diese Anwendung zuerst auf eine frühere Version neu installieren.
1. [!UICONTROL Rollback] Datenbank mithilfe der lokalen [!UICONTROL Database Dump]und importieren Sie es zurück in [!DNL MariaDB].
1. [!UICONTROL Rollback] den Code über [!DNL Git] auf eine frühere Arbeitsversion umzustellen.

Verwenden [!UICONTROL Snapshots] ist nicht die empfohlene Methode für eine Aktualisierung/geplante Aktivität [!UICONTROL rollbacks/restores], da der Abruf der Daten im Vergleich zu einer lokalen viel länger dauert [!UICONTROL Database Dump], wie oben in Schritt 2 der **Wenn eine [!UICONTROL Rollback] ist erforderlich** Abschnitt.

[!UICONTROL Snapshots] nicht auf dem Knoten/Server gespeichert sind, werden sie in einem separaten Speicherblock gespeichert, und da diese Daten vom Blockspeicher über das Netzwerk an eine neue Festplatte übertragen werden müssen, dauert es lange. Diese neue Festplatte wird dann auf den Knoten gemountet, der zum Abrufen/Import auf die ursprüngliche Festplatte bereit ist, die mit dem Knoten/Server verbunden ist.

Wenn Sie dies mit dem Import einer lokalen [!UICONTROL Database Dump], sind die Daten bereits auf dem Knoten/Server abzurufen, sodass viel Zeit als [!UICONTROL Database Import] ist erforderlich.

## Szenario 2: Momentaufnahme wiederherstellen

Lesen: [Wiederherstellen eines Snapshots zu Adobe Commerce in der Cloud-Infrastruktur](https://devdocs.magento.com/cloud/project/project-webint-snap.html#restore-snapshot) in unserer Entwicklerdokumentation.

>[!NOTE]
>
>Die Erstellung eines Schnappschusses muss unser erster Schritt nach dem Zugriff auf Adobe Commerce über das Cloud-Infrastrukturkonto und vor der Anwendung größerer Änderungen sein. Dies ist eine Best Practice und wird dringend empfohlen.

Lesen: [Erstellen eines Schnappschusses](https://devdocs.magento.com/cloud/project/project-webint-snap.html#create-snapshot) in unserer Entwicklerdokumentation.

## Szenario 3: Keine Momentaufnahme, Build-Stable (SSH-Verbindung verfügbar)

In diesem Abschnitt wird gezeigt, wie Sie eine Umgebung zurücksetzen, wenn Sie keine Momentaufnahme erstellt haben, aber über SSH auf die Umgebung zugreifen können.

Die Schritte sind:

1. Deaktivieren Sie die Konfigurationsverwaltung.
1. Deinstallieren Sie die Adobe Commerce-Software.
1. Setzen Sie die [!DNL git] -Verzweigung.

Führen Sie diese Schritte aus:

* Ihre Adobe Commerce-Installation kehrt zum Vanilla-Status zurück (Datenbank wiederhergestellt, Bereitstellungskonfiguration entfernt; Ordner unter `var` gelöscht).
* Ihre [!DNL git] Die Verzweigung wird in der Vergangenheit auf den gewünschten Status zurückgesetzt.

Lesen Sie die detaillierten Schritte unten.

### Schritt 0 (Voraussetzung): Entfernen Sie config.php, um die Konfigurationsverwaltung zu deaktivieren

Wir müssen Configuration Management deaktivieren, damit die vorherigen Konfigurationseinstellungen während der Bereitstellung nicht automatisch angewendet werden.

Um die Konfigurationsverwaltung zu deaktivieren, stellen Sie sicher, dass Ihr `/app/etc/` enthält nicht die `config.php` -Datei.

Gehen Sie wie folgt vor, um die Konfigurationsdatei zu entfernen:

1. [SSH in Ihrer Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Entfernen Sie die Konfigurationsdatei: `rm app/etc/config.php`

Weitere Informationen zur Konfigurationsverwaltung:

* [Reduzieren von Bereitstellungsausfällen in Adobe Commerce in der Cloud-Infrastruktur](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) in unserer Wissensdatenbank.
* [Konfigurationsverwaltung für Speichereinstellungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) in unserer Entwicklerdokumentation.

### Schritt 1: Deinstallieren Sie die Adobe Commerce-Software mit setup:uninstall-Befehl


Durch das Deinstallieren der Adobe Commerce-Software wird die Datenbank gelöscht, die Bereitstellungskonfiguration entfernt und die Ordner unter `var`.

Lesen: [Deinstallieren der Adobe Commerce-Software](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html) in unserer Entwicklerdokumentation.

Gehen Sie wie folgt vor, um die Adobe Commerce-Software zu deinstallieren:

1. [SSH in Ihrer Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Ausführen `setup:uninstall` : `bin/magento setup:uninstall`
1. Bestätigen Sie die Deinstallation.

Die folgende Meldung wird angezeigt, um eine erfolgreiche Deinstallation zu bestätigen:

```php
[SUCCESS]: Magento uninstallation complete.
```

Dies bedeutet, dass wir unsere Adobe Commerce-Installation (einschließlich DB) wieder in ihren authentischen Zustand (Vanilla) zurückversetzt haben.

### Schritt 2: Setzen Sie die [!DNL git] Verzweigung

Mit [!DNL git] zurücksetzen, kehren wir den Code in der Vergangenheit auf den gewünschten Status zurück.

1. Klonen Sie die Umgebung in Ihre lokale Entwicklungsumgebung. Sie können den Befehl in die Cloud-Konsole kopieren:    ![copy_git_clone.png](assets/copy_git_clone.png)
1. Rufen Sie den Commits-Verlauf auf. Verwendung `--reverse` , um den Verlauf in umgekehrter Reihenfolge anzuzeigen, um mehr Komfort zu bieten: `git log --reverse`
1. Wählen Sie den Commit-Hash aus, für den Sie gut waren. Um den Code auf seinen authentischen Status (Vanilla) zurückzusetzen, suchen Sie den allerersten Commit, der Ihre Verzweigung (Umgebung) erstellt hat.
   ![Commit-Hash in der Git-Konsole auswählen](assets/select_commit_hash.png)
1. Hard anwenden [!DNL git] reset: `git reset --h <commit_hash>`
1. Push-Änderungen an Server: `git push --force <origin> <branch>`

Nachdem Sie diese Schritte ausgeführt haben, erhalten Sie die [!DNL git] Die Verzweigung wird zurückgesetzt und die gesamte [!DNL git] changelog ist klar. Die letzte [!DNL git] Push-Trigger die erneute Bereitstellung, um alle Änderungen anzuwenden und Adobe Commerce erneut zu installieren.

## Szenario 4: Keine Momentaufnahme; Build beschädigt (keine [!DNL SSH] connection)

In diesem Abschnitt wird gezeigt, wie eine Umgebung zurückgesetzt wird, wenn sie sich in einem kritischen Zustand befindet: Das Implementierungsverfahren kann beim Erstellen einer Arbeitsanwendung nicht erfolgreich sein, sodass die [!DNL SSH] Verbindung nicht verfügbar.

In diesem Szenario müssen Sie zunächst den Arbeitsstatus Ihrer Adobe Commerce-Anwendung wiederherstellen, indem Sie [!DNL git] die Adobe Commerce-Software zurücksetzen und deinstallieren (zum Ablegen und Wiederherstellen der Datenbank, zur Entfernung der Bereitstellungskonfiguration usw.). Das Szenario umfasst dieselben Schritte wie in Szenario 3, aber die Reihenfolge der Schritte ist anders und es gibt einen zusätzlichen Schritt - &quot;Erzwingen der erneuten Bereitstellung&quot;. Die Schritte sind:

1. [Setzen Sie die [!DNL git] -Verzweigung.](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)
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

Wenn die `setup:uninstall` -Befehl mit einem Fehler fehlschlägt und nicht abgeschlossen werden kann, können wir die DB mit den folgenden Schritten manuell löschen:

1. [SSH in Ihrer Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Stellen Sie eine Verbindung zur MySQL DB her: `mysql -h database.internal` (Für Pro-Umgebungen siehe: [MySQL-Dienst einrichten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html)).
1. Legen Sie die DB \`main\` ab: `drop database main;`
1. Erstellen Sie eine leere DB mit der Bezeichnung &quot;\`main\`&quot;: `create database main;`
1. Löschen Sie die folgenden Konfigurationsdateien: `config.php` , `config.php` , `.bak,` , `env.php`, `env.php.bak`

Nach dem Zurücksetzen der DB [erstellen [!DNL git] Push in die Umgebung zur erneuten Bereitstellung des Triggers](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli.html) und installieren Sie Adobe Commerce in einer neu erstellten DB. Oder [Führen Sie den Befehl redeploy aus](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#environment-commands).
