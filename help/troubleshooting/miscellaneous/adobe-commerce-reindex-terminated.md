---
title: '"Adobe Commerce cloud: reindex wird mit der Meldung "Killed" beendet'
description: "* Adobe Commerce auf Cloud-Infrastruktur (alle Versionen)"
exl-id: 36ed9c9f-8280-41db-9df3-fe842dade4b1
feature: Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Adobe Commerce Cloud: Neuindizierung wird mit `Killed`-Meldung beendet

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur (alle Versionen)

## Problem

Sie versuchen, eine Neuindizierung im Integrationszweig (oder im Staging des Starter-Architekturprojekts) auszuführen, und der Prozess wird mit der Meldung `Killed` beendet.

## Ursache

Dies geschieht normalerweise, weil den PHP-Prozessen der Arbeitsspeicher ausgeht.
Der häufigste Grund dafür ist eine große Anzahl von Produkten, Geschäften und/oder Kundengruppen in der Instanz.

## Lösung

1. Reduzieren Sie die Anzahl der Produkte (sowie ggf. Kundengruppen und Stores).
1. Beschränken Sie die Verwendung auf einen oder zwei gleichzeitige Benutzer.
1. Deaktivieren Sie Cron-Aufträge und führen Sie sie nach Bedarf manuell aus.
1. Wenn dies noch nicht geschehen ist, fordern Sie eine Aktualisierung auf die Umgebungen für die erweiterte Integration an. Beachten Sie die Einschränkung hinsichtlich der Anzahl der Umgebungen, auf die Sie nach der Aktualisierung beschränkt sind. Weitere Informationen finden Sie im Artikel [Verbesserungsanfrage zur Integrationsumgebung - Pro und Starter](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) in unserer Support-Wissensdatenbank.

## Verwandtes Lesen:

In unserer Entwicklerdokumentation:

* [Pro-Architektur > Integrationsumgebung](https://devdocs.magento.com/cloud/architecture/pro-architecture.html#cloud-arch-int)
* [Starterarchitektur > Staging-Umgebung](https://devdocs.magento.com/cloud/architecture/starter-architecture.html#cloud-arch-stage)
