---
title: Geringer Festplattenspeicher
description: In diesem Artikel werden Lösungen für die Situation vorgeschlagen, in der Ihnen in einer bestimmten Umgebung von Adobe Commerce in der Cloud-Infrastruktur der Speicherplatz ausgeht.
exl-id: 1b2c25d3-ca1b-4409-8d6b-378aa0952f94
feature: Storage, Observability
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Geringer Festplattenspeicher

In diesem Artikel werden Lösungen für die Situation vorgeschlagen, in der Ihnen in einer bestimmten Umgebung von Adobe Commerce in der Cloud-Infrastruktur der Speicherplatz ausgeht.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle [unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Ihnen geht der Speicherplatz auf der Festplatte mit beschreibbaren Verzeichnissen aus. Ein Symptom kann die [hängende Bereitstellung](/help/troubleshooting/deployment/deployment-stuck-with-unable-to-upload-the-application-to-the-remote-cluster-error.md) sein.

Führen Sie den folgenden Befehl aus, um die Festplattenauslastung zu überprüfen:

```bash
df -h var/
```

## Ursache

Das Verzeichnis `var` ist normalerweise das Verzeichnis, das viel Platz in Anspruch nehmen und leicht bereinigt werden kann.

Adobe Commerce speichert alle Protokolldateien im Ordner &quot;`var`&quot;. Neue Protokolldateien werden erstellt und alte werden täglich archiviert. Wenn jedoch die Anzahl der generierten Fehler weiter zunimmt, nehmen Protokolldateien immer mehr Platz in Anspruch.

Benutzerdefinierte Import-/Exportdateien werden ebenfalls im Verzeichnis `var` gespeichert und nehmen Platz, wenn die Anzahl steigt.

## Lösung

Lösungsoptionen:

* Überprüfen Sie, ob Sie große Protokolldateien haben und untersuchen Sie, warum sie groß sind, und beheben Sie das Problem, das eine große Menge an Protokollausgabe generiert.
* Bereinigen Sie das Verzeichnis `var` .
* Richten Sie einen Cron-Auftrag ein, um die Größe des Verzeichnisses `var` zu verfolgen und zu bereinigen.
* Weisen Sie mehr Speicherplatz zu, wenn Sie noch nicht genügend Speicherplatz haben. (Im folgenden Abschnitt erfahren Sie, wie Sie überprüfen können, welche Leerzeichen Sie einschließen.)
   * Für Starter-Pläne, alle Umgebungen und Pro-Plan-Integrationsumgebungen können Sie den Speicherplatz zuweisen, wenn Sie nicht belegt sind, wie unter [Speicherplatz verwalten: Festplattenspeicher zuweisen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#application-disk-space) beschrieben.
   * Wenden Sie sich für Staging- und Produktionsumgebungen mit Pro-Plan an den Support, um mehr Speicherplatz zuzuweisen, wenn Sie noch nicht genügend Speicherplatz haben.
* Wenn Sie Ihre Speicherplatzbeschränkung erreicht haben und dennoch Probleme mit wenig Speicherplatz auftreten, sollten Sie sich für weitere Informationen an Ihr Adobe Account Team wenden.

### Überprüfen der Festplattenspeicherplatzbegrenzung

So prüfen Sie, wie viel Platz Sie für die einzelnen Adobe Commerce in der Cloud-Infrastruktur-Umgebung haben:

1. Melden Sie sich bei der [Cloud-Konsole](https://console.adobecommerce.com) an.
1. Wählen Sie im Dashboard **[!UICONTROL All projects]** das entsprechende Projekt aus. In der linken Ecke sehen Sie die Verfügbarkeit des Festplattenspeichers.

   ![project_space.png](/help/troubleshooting/miscellaneous/assets/project_space.png)
