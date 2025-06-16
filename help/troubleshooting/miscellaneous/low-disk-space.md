---
title: Geringer Festplattenspeicher
description: In diesem Artikel werden Lösungen für die Situation vorgeschlagen, wenn Ihnen in einer bestimmten Umgebung von Adobe Commerce in der Cloud-Infrastruktur der Speicherplatz ausgeht.
exl-id: 1b2c25d3-ca1b-4409-8d6b-378aa0952f94
feature: Storage, Observability
role: Developer
source-git-commit: 842c329b5d8bacf72ac689412fde5a5d76d16e85
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Geringer Festplattenspeicher

In diesem Artikel werden Lösungen für die Situation vorgeschlagen, wenn Ihnen in einer bestimmten Umgebung von Adobe Commerce in der Cloud-Infrastruktur der Speicherplatz ausgeht.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle [unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Es ist nicht mehr genügend Speicherplatz auf der Festplatte mit beschreibbaren Verzeichnissen vorhanden. Ein Symptom kann sein [stecken geblieben](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26878).

Um die Festplattenauslastung zu überprüfen, führen Sie den folgenden Befehl aus:

```bash
df -h var/
```

## Ursache

Das `var` ist normalerweise das Verzeichnis, das viel Platz in Anspruch nehmen kann und leicht bereinigt werden kann.

Adobe Commerce speichert alle Protokolldateien im `var`. Neue Protokolldateien werden erstellt und alte täglich archiviert. Wenn die Anzahl der generierten Fehler jedoch weiter steigt, nehmen Protokolldateien mehr und mehr Speicherplatz ein.

Benutzerdefinierte Import-/Exportdateien werden ebenfalls im `var` gespeichert und nehmen Speicherplatz in Anspruch, wenn ihre Anzahl zunimmt.

## Lösung

Lösungsoptionen:

* Überprüfen Sie, ob Sie große Protokolldateien haben, und untersuchen Sie, warum sie groß sind. Beheben Sie das Problem, indem Sie eine große Menge an Protokollausgaben generieren.
* Bereinigen Sie das `var`.
* Richten Sie einen Cron-Auftrag ein, um die Größe des `var` zu verfolgen und zu bereinigen.
* Weisen Sie mehr Speicherplatz zu, wenn Sie nicht verwendeten Speicherplatz haben. (Im folgenden Abschnitt finden Sie Informationen dazu, wie Sie Ihre Speicherplatzbeschränkung überprüfen können.)
   * Für den Starter-Plan, alle Umgebungen und Pro-Plan-Integrationsumgebungen können Sie den Speicherplatz zuweisen, wenn Sie ungenutzten Speicherplatz haben, wie in [Verwalten von Speicherplatz: Zuweisen von Speicherplatz](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#application-disk-space) beschrieben.
   * Bei Pro Plan Staging- und Produktionsumgebungen wenden Sie sich an den Support, um mehr Speicherplatz zuzuweisen, wenn Sie ungenutzte Ressourcen haben.
* Wenn Sie Ihr Speicherplatzlimit erreicht haben und weiterhin Probleme mit wenig Speicherplatz haben, sollten Sie ggf. weiteren Speicherplatz kaufen. Weitere Informationen erhalten Sie von Ihrem Adobe-Account-Team.

### Überprüfen des Speicherplatzlimits

So überprüfen Sie, wie viel Speicherplatz Sie für jede Adobe Commerce in der Cloud-Infrastrukturumgebung haben:

1. Melden Sie sich bei der [Cloud-Konsole](https://console.adobecommerce.com) an.
1. Wählen Sie im **[!UICONTROL All projects]**-Dashboard das entsprechende Projekt aus. In der linken Ecke sehen Sie die Verfügbarkeit von Speicherplatz.

   ![project_space.png](/help/troubleshooting/miscellaneous/assets/project_space.png)
