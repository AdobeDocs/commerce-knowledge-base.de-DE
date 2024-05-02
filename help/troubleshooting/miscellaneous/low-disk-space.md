---
title: Geringer Festplattenspeicher
description: In diesem Artikel werden Lösungen für die Situation vorgeschlagen, in der Ihnen in einer bestimmten Umgebung von Adobe Commerce in der Cloud-Infrastruktur der Speicherplatz ausgeht.
exl-id: 1b2c25d3-ca1b-4409-8d6b-378aa0952f94
feature: Storage, Observability
role: Developer
source-git-commit: 9ee4145d5516a37fab1c092d539000627f242a93
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Geringer Festplattenspeicher

In diesem Artikel werden Lösungen für die Situation vorgeschlagen, in der Ihnen in einer bestimmten Umgebung von Adobe Commerce in der Cloud-Infrastruktur der Speicherplatz ausgeht.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle [unterstützte Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Ihnen geht der Speicherplatz auf der Festplatte mit beschreibbaren Verzeichnissen aus. Ein Symptom kann [hängengebliebene Bereitstellung](/help/troubleshooting/deployment/deployment-stuck-with-unable-to-upload-the-application-to-the-remote-cluster-error.md).

Führen Sie den folgenden Befehl aus, um die Festplattenauslastung zu überprüfen:

```bash
df -h var/
```

## Ursache

Die `var` -Verzeichnis ist normalerweise derjenige, der viel Speicherplatz in Anspruch nehmen und leicht bereinigt werden kann.

Adobe Commerce speichert alle Protokolldateien im `var` Verzeichnis. Neue Protokolldateien werden erstellt und alte werden täglich archiviert. Wenn jedoch die Anzahl der generierten Fehler weiter zunimmt, nehmen Protokolldateien immer mehr Platz in Anspruch.

Benutzerdefinierte Import-/Exportdateien werden ebenfalls im `var` und Platz nehmen, wenn die Anzahl steigt.

## Lösung

Lösungsoptionen:

* Überprüfen Sie, ob Sie große Protokolldateien haben und untersuchen Sie, warum sie groß sind, und beheben Sie das Problem, das eine große Menge an Protokollausgabe generiert.
* Reinigen Sie die `var` Verzeichnis.
* Richten Sie einen Cron-Auftrag ein, um die Größe der `var` und bereinigen Sie es.
* Weisen Sie mehr Speicherplatz zu, wenn Sie noch nicht genügend Speicherplatz haben. (Im folgenden Abschnitt erfahren Sie, wie Sie überprüfen können, welche Leerzeichen Sie einschließen.)
   * Für Starter-Pläne, alle Umgebungen und Pro-Plan-Integrationsumgebungen können Sie den Festplattenspeicher zuweisen, wenn Sie nicht belegt sind, wie unter [Speicherplatz verwalten: Festplattenspeicher zuweisen](https://devdocs.magento.com/guides/v2.3/cloud/project/manage-disk-space.html#application-disk-space).
   * Wenden Sie sich für Staging- und Produktionsumgebungen mit Pro-Plan an den Support, um mehr Speicherplatz zuzuweisen, wenn Sie noch nicht genügend Speicherplatz haben.
* Wenn Sie Ihre Speicherplatzbeschränkung erreicht haben und dennoch Probleme mit wenig Speicherplatz auftreten, sollten Sie sich für weitere Informationen an Ihr Adobe Account Team wenden.

### Überprüfen der Festplattenspeicherplatzbegrenzung

So prüfen Sie, wie viel Platz Sie für die einzelnen Adobe Commerce in der Cloud-Infrastruktur-Umgebung haben:

1. Melden Sie sich bei [Cloud-Konsole](https://console.adobecommerce.com).
1. Im **[!UICONTROL All projects]** Dashboard das entsprechende Projekt auswählen. In der linken Ecke sehen Sie die Verfügbarkeit des Festplattenspeichers.

   ![project_space.png](/help/troubleshooting/miscellaneous/assets/project_space.png)
