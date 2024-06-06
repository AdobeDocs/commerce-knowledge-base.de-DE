---
title: Zurücksetzen der Umgebung ohne Cloud-Schnappschuss
description: In diesem Artikel werden zwei Lösungen vorgestellt, um eine Umgebung wiederherzustellen, ohne dass eine Momentaufnahme Ihrer Umgebung in Adobe Commerce in der Cloud-Infrastruktur vorliegt.
exl-id: 834d13a7-3b1a-460c-9ed0-9d560105f436
feature: Build, Cloud, Console
source-git-commit: 5347e8714ef1374440f5d246100a0221e4b189fc
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# Zurücksetzen der Umgebung ohne Cloud-Schnappschuss

In diesem Artikel werden zwei Lösungen vorgestellt, um eine Umgebung wiederherzustellen, ohne dass eine Momentaufnahme Ihrer Umgebung in Adobe Commerce in der Cloud-Infrastruktur vorliegt.

## Betroffene Produkte und Versionen

* Adobe Commerce zur Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Wählen Sie die für Ihren Fall am besten geeignete Option aus:

* Wenn Sie einen stabilen Build haben, aber keinen gültigen Schnappschuss - [Szenario 1: Keine Momentaufnahme, Build-Stable (SSH-Verbindung verfügbar)](#scen2).
* Wenn der Build beschädigt ist und Sie keinen gültigen Schnappschuss haben - [Szenario 2: Keine Momentaufnahme; Build defekt (keine SSH-Verbindung)](#scen3).

## Szenario 1: Keine Momentaufnahme, Build-Stable (SSH-Verbindung verfügbar) {#scen2}

In diesem Abschnitt erfahren Sie, wie Sie eine Umgebung wiederherstellen, wenn Sie keinen Schnappschuss erstellt haben, aber über SSH auf die Umgebung zugreifen können.

Die Schritte sind:

1. Deaktivieren Sie die Konfigurationsverwaltung.
1. Deinstallieren Sie die Adobe Commerce-Software.
1. Setzen Sie die Git-Verzweigung zurück.

Führen Sie diese Schritte aus:

* Ihre Adobe Commerce-Installation kehrt zum Vanilla-Status zurück (Datenbank wiederhergestellt, Bereitstellungskonfiguration entfernt; Ordner unter `var` gelöscht)
* Ihre Git-Verzweigung wird in der Vergangenheit auf den gewünschten Status zurückgesetzt

Gehen Sie wie folgt vor:

### Schritt 0 (Voraussetzung): Entfernen Sie config.php, um die Konfigurationsverwaltung zu deaktivieren {#disable_config_management}

Wir müssen Configuration Management deaktivieren, damit die vorherigen Konfigurationseinstellungen während der Bereitstellung nicht automatisch angewendet werden.

Um die Konfigurationsverwaltung zu deaktivieren, stellen Sie sicher, dass Ihr `/app/etc/` enthält nicht die `config.php` (für Adobe Commerce 2.4.x) oder `config.local.php` (für Adobe Commerce 2.1.x).

Gehen Sie wie folgt vor, um die Konfigurationsdatei zu entfernen:

1. [SSH in Ihrer Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
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

* [Reduzieren von Bereitstellungsausfällen in Adobe Commerce in der Cloud-Infrastruktur](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) in unserer Wissensdatenbank.
* [Konfigurationsverwaltung für Speichereinstellungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) in unserer Entwicklerdokumentation.

### Schritt 1: Deinstallieren Sie die Adobe Commerce-Software mit setup:uninstall-Befehl {#setup-uninstall}


Durch das Deinstallieren der Adobe Commerce-Software wird die Datenbank gelöscht, die Bereitstellungskonfiguration entfernt und die Ordner unter `var`.

Überprüfen [Deinstallieren der Adobe Commerce-Software](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html) in unserer Entwicklerdokumentation.

Gehen Sie wie folgt vor, um die Adobe Commerce-Software zu deinstallieren:

1. [SSH in Ihrer Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Ausführen `setup:uninstall`:

   ```php
     php bin/magento setup:uninstall
   ```

1. Bestätigen Sie die Deinstallation.

Die folgende Meldung wird angezeigt, um eine erfolgreiche Deinstallation zu bestätigen:

```php
[SUCCESS]: Magento uninstallation complete.
```

Dies bedeutet, dass wir unsere Adobe Commerce-Installation (einschließlich DB) wieder in ihren authentischen Zustand (Vanilla) zurückversetzt haben.

### Schritt 2: Git-Verzweigung zurücksetzen {#reset-git-branch}

Beim Zurücksetzen von Git kehren wir den Code in der Vergangenheit zum gewünschten Status zurück.

1. Klonen Sie die Umgebung in Ihre lokale Entwicklungsumgebung. Sie können den Befehl in die Cloud-Konsole kopieren:    ![copy_git_clone.png](assets/copy_git_clone.png)
1. Rufen Sie den Commits-Verlauf auf. Verwendung `--reverse` , um den Verlauf in umgekehrter Reihenfolge anzuzeigen, um mehr Komfort zu bieten:

   ```git
     git log --reverse
   ```

1. Wählen Sie den Commit-Hash aus, für den Sie gut waren. Um den Code auf seinen authentischen Status (Vanilla) zurückzusetzen, suchen Sie den allerersten Commit, der Ihre Verzweigung (Umgebung) erstellt hat.    ![Commit-Hash in der Git-Konsole auswählen](assets/select_commit_hash.png)
1. Wenden Sie das Hard Git-Reset an:

   ```git
     git reset --h <commit_hash>
   ```

1. Push-Änderungen an Server:

   ```git
     git push --force <origin> <branch>
   ```

Nachdem Sie diese Schritte ausgeführt haben, wird unsere Git-Verzweigung zurückgesetzt und der gesamte Git-Änderungsprotokoll ist klar. Die letzte Git-Push-Trigger führt die erneute Bereitstellung durch, um alle Änderungen anzuwenden und Adobe Commerce neu zu installieren.

## Szenario 2: Keine Momentaufnahme; Build defekt (keine SSH-Verbindung) {#scen3}

In diesem Abschnitt wird gezeigt, wie eine Umgebung in einem kritischen Zustand zurückgesetzt wird: Das Implementierungsverfahren kann beim Erstellen einer funktionierenden Anwendung nicht erfolgreich sein, sodass die SSH-Verbindung nicht verfügbar ist.

In diesem Szenario müssen Sie zunächst den Arbeitsstatus Ihrer Adobe Commerce-Anwendung mithilfe des Git-Resets wiederherstellen und dann die Adobe Commerce-Software deinstallieren (um die Datenbank abzulegen und wiederherzustellen, die Bereitstellungskonfiguration zu entfernen usw.). Das Szenario umfasst dieselben Schritte wie in Szenario 1, aber die Reihenfolge der Schritte ist anders und es gibt einen zusätzlichen Schritt - &quot;Erzwingen der erneuten Bereitstellung&quot;. Die Schritte sind:

[1. Setzen Sie die Git-Verzweigung zurück.](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)

[2. Deaktivieren Sie die Konfigurationsverwaltung.](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)

[3. Deinstallieren Sie die Adobe Commerce-Software.](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)

4&amp;period; Neuverlegung erzwingen.

Nachdem Sie diese Schritte ausgeführt haben, haben Sie dieselben Ergebnisse wie in Szenario 1.

### Schritt 4: Erzwingen der erneuten Bereitstellung

Erstellen Sie einen Commit (dies kann ein leerer Commit sein, obwohl wir ihn nicht empfehlen) und pushen Sie ihn auf den Server, um eine erneute Bereitstellung des Triggers durchzuführen:

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## Wenn Setup:uninstall fehlschlägt, die Datenbank manuell zurücksetzen

Wenn die `setup:uninstall` -Befehl mit einem Fehler fehlschlägt und nicht abgeschlossen werden kann, können wir die DB mit den folgenden Schritten manuell löschen:

1. [SSH in Ihrer Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Stellen Sie eine Verbindung zur MySQL DB her:

   ```sql
   mysql -h database.internal
   ```

1. Legen Sie die `main` DB:

   ```sql
   drop database main;
   ```

1. Leere erstellen `main` DB:

   ```sql
   create database main;
   ```

1. Löschen Sie die folgenden Konfigurationsdateien: `config.php`, `config.php` `.bak`, `env.php`, und `env.php.bak`.

Nach dem Zurücksetzen der DB [einen Git-Push in die Umgebung durchführen, um die erneute Bereitstellung des Triggers zu ermöglichen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#git-commands) und installieren Sie Adobe Commerce in einer neu erstellten DB. Oder [Führen Sie den Befehl redeploy aus](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#environment-commands).

## Verwandtes Lesen

In unserer Entwicklerdokumentation:

* [Wiederherstellen eines Snapshots in Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup)
* [Erstellen eines Schnappschusses](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#create-a-manual-backup)
* [Snapshots und Backup-Verwaltung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)
* [Verwalten von Zweigen mit der Cloud Console - Protokolle anzeigen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html?lang=en#view-logs)
* [Komponentenbereitstellungsfehler](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/recover-failed-deployment.html)
* [Projekt verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project)
