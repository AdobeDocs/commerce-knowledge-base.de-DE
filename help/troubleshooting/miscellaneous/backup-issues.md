---
title: Backup-Probleme
description: In diesem Artikel werden die möglichen Lösungen für die Probleme bei der Erstellung von Backups aufgeführt.
exl-id: 1a6204ad-bd5a-46dc-8a8e-39655a174e09
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Backup-Probleme

In diesem Artikel werden die möglichen Lösungen für die Probleme bei der Erstellung von Backups aufgeführt.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.3.x
* Magento Open Source 2.3.x

## Sicherung deaktiviert {#backup-disabled}

Wenn die Adobe Commerce-Sicherungsfunktion nicht gestartet wird oder die folgende Meldung angezeigt wird, müssen Sie die Funktion vor dem Sichern aktivieren.

```bash
Backup functionality is disabled.
Backup functionality is currently disabled. Please use other means for backups.
```

Geben Sie den folgenden CLI-Befehl ein:

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

Weitere Informationen zu Backups finden Sie unter [Sichern und Zurücksetzen des Dateisystems, der Medien und der Datenbank.](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/tutorials/backup)

## Nicht genügend Speicherplatz {#insufficient-disk-space-trouble-backup-space-}

Wenn das Backup aufgrund von ungenügendem Speicherplatz fehlschlug, sollten Sie in der Regel Speicherplatz freigeben, indem Sie einige Dateien auf ein anderes Speichergerät oder Laufwerk verschieben. Es kann jedoch andere Möglichkeiten geben, das Problem zu beheben. Tipps finden Sie in einer der folgenden Ressourcen:

* [8 Tipps zur Lösung von Problemen mit der Festplatte von Linux- und Unix-Systemen, z. B. Volle Festplatte oder Schreibfehler auf der Festplatte](https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk)
* [ServerFault: DF gibt an, dass die Festplatte voll ist, dies ist aber nicht der Fall](https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not)
* [unix.stackexchange.com: Verfolgen Sie, wo auf Linux Speicherplatz verschwunden ist?](https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux)

## Betriebssystemfehler {#operating-system-error-trouble-backup-os-}

Leider können wir aufgrund der Vielzahl der Fehler, auf die Sie stoßen können, keine spezifischen Empfehlungen aussprechen. Wir können Ihnen jedoch folgendes vorschlagen:

* Wenden Sie sich an Ihren Systemadministrator.
* Öffentliche Foren wie &quot;[ Exchange“ ](https://unix.stackexchange.com) &quot;[ Overflow](https://stackoverflow.com) durchsuchen
* Öffnen Sie ein [GitHub-Problem](https://github.com/magento/magento2/issues) und wir versuchen, Ihnen zu helfen.

## Backup schlägt fehl {#backup-fails-trouble-backup-all-}

Wenn das Backup fehlschlägt oder alle Backup-Tests fehlschlagen, verfügt der [Adobe Commerce-](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/prerequisites/file-system/overview) möglicherweise nicht über ausreichende Berechtigungen und Eigentümerrechte für das Adobe Commerce-Dateisystem. Beispielsweise könnte ein anderer Benutzer Eigentümer der Dateien sein, oder die Dateien sind schreibgeschützt.

Achten Sie besonders auf Dateisystemberechtigungen und die Eigentümerschaft des `<magento_root>/var` und der Unterverzeichnisse. Weitere Informationen finden Sie unter [Festlegen von Dateisystemberechtigungen und Eigentümerschaft](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/prerequisites/file-system/configure-permissions).
