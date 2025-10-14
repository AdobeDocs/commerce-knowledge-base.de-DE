---
title: Rollback der Umgebung ohne Cloud-Snapshot
description: Dieser Artikel zeigt zwei Lösungen zum Zurücksetzen einer Umgebung, ohne dass eine Momentaufnahme Ihrer Umgebung in Adobe Commerce in der Cloud-Infrastruktur vorhanden ist.
exl-id: 834d13a7-3b1a-460c-9ed0-9d560105f436
feature: Build, Cloud, Console
source-git-commit: 5347e8714ef1374440f5d246100a0221e4b189fc
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# Rollback der Umgebung ohne Cloud-Snapshot

Dieser Artikel zeigt zwei Lösungen zum Zurücksetzen einer Umgebung, ohne dass eine Momentaufnahme Ihrer Umgebung in Adobe Commerce in der Cloud-Infrastruktur vorhanden ist.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Wählen Sie das für Ihren Fall am besten geeignete aus:

* Wenn Sie einen stabilen Build, aber keinen gültigen Snapshot haben - ([&#x200B; 1: Kein Snapshot, Build stabil (SSH-Verbindung verfügbar)](#scen2).
* Wenn der Build beschädigt ist und Sie keinen gültigen Snapshot haben - [Szenario 2: Kein Snapshot; Build beschädigt (keine SSH-Verbindung)](#scen3).

## Szenario 1: Kein Snapshot, Build stabil (SSH-Verbindung verfügbar) {#scen2}

In diesem Abschnitt wird gezeigt, wie eine Umgebung zurückgesetzt werden kann, wenn Sie keinen Snapshot erstellt haben, aber über SSH auf die Umgebung zugreifen können.

Die Schritte sind:

1. Deaktivieren Sie die Konfigurationsverwaltung.
1. Deinstallieren Sie die Adobe Commerce-Software.
1. Zurücksetzen der Git-Verzweigung.

Nachdem Sie diese Schritte ausgeführt haben:

* Ihre Adobe Commerce-Installation kehrt in den Vanilla-Status zurück (Datenbank wiederhergestellt; Bereitstellungskonfiguration entfernt; Verzeichnisse unter `var` gelöscht)
* Die Git-Verzweigung wurde in der Vergangenheit auf den gewünschten Status zurückgesetzt

Lesen Sie die folgenden detaillierten Schritte:

### Schritt 0 (Voraussetzung): Entfernen Sie config.php, um die Konfigurationsverwaltung zu deaktivieren {#disable_config_management}

Wir müssen die Konfigurationsverwaltung deaktivieren, damit sie während der Bereitstellung nicht automatisch die vorherigen Konfigurationseinstellungen anwendet.

Um die Konfigurationsverwaltung zu deaktivieren, stellen Sie sicher, dass Ihr `/app/etc/`-Verzeichnis nicht die `config.php` (für Adobe Commerce 2.4.x) oder `config.local.php` (für Adobe Commerce 2.1.x) enthält.

Gehen Sie wie folgt vor, um die Konfigurationsdatei zu entfernen:

1. [SSH in Ihre Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=de).
1. Entfernen Sie die Konfigurationsdatei:
   * Für Adobe Commerce 2.4:

   ```php
    rm app/etc/config.php
   ```

   * Für Adobe Commerce 2.1:

   ```php
     rm app/etc/config.local.php
   ```

Weitere Informationen zur Konfigurationsverwaltung finden Sie unter:

* [Verkürzen Sie Bereitstellungsausfälle auf Adobe Commerce auf Cloud](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md)Infrastrukturen in unserer Support-Wissensdatenbank.
* [Konfigurationsverwaltung für Store-Einstellungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=de) in unserer Entwicklerdokumentation.

### Schritt 1: Deinstallieren Sie die Adobe Commerce-Software mit dem Befehl setup:uninstall {#setup-uninstall}


Durch die Deinstallation der Adobe Commerce-Software wird die Datenbank gelöscht, die Bereitstellungskonfiguration entfernt und die Ordner unter `var` gelöscht.

Lesen Sie [Adobe Commerce-Software deinstallieren](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html?lang=de) in unserer Entwicklerdokumentation.

Gehen Sie wie folgt vor, um die Adobe Commerce-Software zu deinstallieren:

1. [SSH in Ihre Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=de).
1. `setup:uninstall` ausführen:

   ```php
     php bin/magento setup:uninstall
   ```

1. Deinstallation bestätigen.

Die folgende Meldung wird angezeigt, um eine erfolgreiche Deinstallation zu bestätigen:

```php
[SUCCESS]: Magento uninstallation complete.
```

Dies bedeutet, dass wir unsere Adobe Commerce-Installation (einschließlich DB) in ihren authentischen (Vanilla-)Status zurückgesetzt haben.

### Schritt 2: Git-Verzweigung zurücksetzen {#reset-git-branch}

Beim Zurücksetzen von Git stellen wir den Code in den gewünschten Status in der Vergangenheit zurück.

1. Klonen Sie die Umgebung in Ihre lokale Entwicklungsumgebung. Sie können den Befehl in die Cloud-Konsole kopieren:    ![copy_git_clone.png](assets/copy_git_clone.png)
1. Zugriff auf den Commit-Verlauf. `--reverse` verwenden, um den Verlauf zur Vereinfachung in umgekehrter Reihenfolge anzuzeigen:

   ```git
     git log --reverse
   ```

1. Wählen Sie den Commit-Hash aus, für den Sie gut waren. Um den Code in seinen authentischen Zustand (Vanilla) zurückzusetzen, suchen Sie den ersten Commit, mit dem Ihre Verzweigung (Umgebung) erstellt wurde.    ![Commit-Hash in der Git-Konsole auswählen](assets/select_commit_hash.png)
1. Anwenden des harten Git-Zurücksetzungsprozesses:

   ```git
     git reset --h <commit_hash>
   ```

1. Änderungen an Server pushen:

   ```git
     git push --force <origin> <branch>
   ```

Nach dem Ausführen dieser Schritte wird unsere Git-Verzweigung zurückgesetzt und das gesamte Git-Änderungsprotokoll ist gelöscht. Die letzten Git-Push-Trigger stellen Adobe Commerce erneut bereit, um alle Änderungen anzuwenden und neu zu installieren.

## Szenario 2: Kein Snapshot; Build beschädigt (keine SSH-Verbindung) {#scen3}

In diesem Abschnitt wird gezeigt, wie eine Umgebung in einem kritischen Zustand zurückgesetzt werden kann: Das Bereitstellungsverfahren kann keine funktionierende Anwendung erstellen, wodurch die SSH-Verbindung nicht verfügbar wird.

In diesem Szenario müssen Sie zunächst den Arbeitsstatus Ihrer Adobe Commerce-Anwendung mithilfe des Git-Resets wiederherstellen und dann die Adobe Commerce-Software deinstallieren (um die Datenbank abzulegen und wiederherzustellen, die Bereitstellungskonfiguration zu entfernen usw.). Das Szenario umfasst dieselben Schritte wie in Szenario 1, aber die Reihenfolge der Schritte unterscheidet sich, und es gibt einen zusätzlichen Schritt: Erzwingen der erneuten Bereitstellung. Die Schritte sind:

[1. Setzen Sie die Git-Verzweigung zurück.](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)

[2. Deaktivieren Sie die Konfigurationsverwaltung.](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)

[3. Deinstallieren Sie die Adobe Commerce-Software.](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)

4&Zeitraum; Erzwingen der erneuten Bereitstellung.

Nachdem Sie diese Schritte ausgeführt haben, erhalten Sie dieselben Ergebnisse wie in Szenario 1.

### Schritt 4: Erzwingen der erneuten Bereitstellung

Führen Sie einen Commit durch (dies kann ein leerer Commit sein, obwohl wir dies nicht empfehlen) und übertragen Sie ihn auf den -Server, um den Trigger erneut bereitzustellen:

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## Wenn setup:uninstall fehlschlägt, Datenbank manuell zurücksetzen

Wenn die Ausführung des `setup:uninstall`-Befehls mit einem Fehler fehlschlägt und nicht abgeschlossen werden kann, können wir die Datenbank mit diesen Schritten manuell löschen:

1. [SSH in Ihre Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=de).
1. Verbindung zur MySQL-DB herstellen:

   ```sql
   mysql -h database.internal
   ```

1. `main` DB ablegen:

   ```sql
   drop database main;
   ```

1. Leere `main`-DB erstellen:

   ```sql
   create database main;
   ```

1. Löschen Sie die folgenden Konfigurationsdateien: `config.php`, `config.php` `.bak`, `env.php` und `env.php.bak`.

Nach dem Zurücksetzen der DB [&#x200B; Sie „einen Git-Push an die Umgebung durchführen, um den Trigger erneut bereitzustellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html?lang=de#git-commands) und Adobe Commerce in einer neu erstellten DB zu installieren. Oder [führen Sie den Befehl zum erneuten Bereitstellen &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html?lang=de#environment-commands).

## Verwandtes Lesen

In unserer Entwicklerdokumentation:

* [Einen Schnappschuss in der Cloud wiederherstellen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup)
* [Snapshot erstellen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#create-a-manual-backup)
* [Snapshots und Backup-Verwaltung](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)
* [Verzweigungen mit der Cloud-Konsole verwalten - Protokolle anzeigen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html?lang=de#view-logs)
* [Fehler bei der Komponentenbereitstellung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/recover-failed-deployment.html?lang=de)
* [Projekt verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=de#configure-the-project)
