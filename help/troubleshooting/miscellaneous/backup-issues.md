---
title: Backup-Probleme
description: In diesem Artikel werden die möglichen Lösungen für die Probleme bei der Erstellung von Sicherungskopien aufgelistet.
exl-id: 1a6204ad-bd5a-46dc-8a8e-39655a174e09
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Backup-Probleme

In diesem Artikel werden die möglichen Lösungen für die Probleme bei der Erstellung von Sicherungskopien aufgelistet.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.3.x
* Magento Open Source 2.3.x

## Backup disabled {#backup-disabled}

Wenn die Adobe Commerce-Sicherungsfunktion nicht gestartet wird oder die folgende Meldung angezeigt wird, müssen Sie die Funktion vor der Sicherung aktivieren.

```terminal
Backup functionality is disabled.
Backup functionality is currently disabled. Please use other means for backups.
```

Geben Sie den folgenden CLI-Befehl ein:

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

Weitere Informationen zu Backups finden Sie unter [Sichern Sie das Dateisystem, die Medien und die Datenbank und führen Sie einen Rollback durch.](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-backup.html)

## Unzureichender Festplattenspeicher {#insufficient-disk-space-trouble-backup-space-}

Wenn die Sicherung fehlschlägt, weil nicht genügend Speicherplatz vorhanden ist, sollten Sie normalerweise Speicherplatz freigeben, indem Sie einige Dateien auf ein anderes Speichergerät oder Laufwerk verschieben. Es gibt jedoch möglicherweise andere Möglichkeiten, das Problem zu lösen. Tipps finden Sie in einer der folgenden Ressourcen:

* [8 Tipps zur Lösung von Problemen mit Linux- und Unix-Systemfestplatten wie voll Disk Full oder kann nicht auf die Festplatte schreiben](https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk)
* [serverfailure: df sagt, dass die Festplatte voll ist, aber nicht](https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not)
* [unix.stackexchange.com: Verfolgen Sie, wo auf Linux Speicherplatz gegangen ist?](https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux)

## Betriebssystemfehler {#operating-system-error-trouble-backup-os-}

Leider können wir aufgrund der Vielzahl von Fehlern, auf die Sie stoßen können, keine besonderen Empfehlungen geben. Wir können Ihnen jedoch Folgendes vorschlagen:

* Wenden Sie sich an Ihren Systemadministrator.
* Durchsuchen Sie öffentliche Foren wie [Stack Exchange](https://unix.stackexchange.com) oder [Stapelüberlauf](https://stackoverflow.com)
* Öffnen Sie eine [GitHub-Problem](https://github.com/magento/magento2/issues) und wir werden versuchen zu helfen.

## Backup schlägt fehl {#backup-fails-trouble-backup-all-}

Wenn die Sicherung fehlschlägt oder alle Sicherungstests fehlschlagen, kann die [Adobe Commerce-Dateisysteminhaber](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/file-sys-perms-over.html) verfügt nicht über ausreichende Berechtigungen und Eigentümer des Adobe Commerce-Dateisystems. Beispielsweise könnten die Dateien einem anderen Benutzer gehören oder die Dateien sind möglicherweise schreibgeschützt.

Beachten Sie insbesondere die Dateisystemberechtigungen und das Eigentum an der `<magento_root>/var` Verzeichnis und Unterverzeichnissen. Weitere Informationen finden Sie unter [Festlegen von Dateisystemberechtigungen und -berechtigungen](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-system-perms.html).
