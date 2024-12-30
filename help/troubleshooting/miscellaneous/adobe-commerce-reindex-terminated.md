---
title: 'Adobe Commerce Cloud: Neuindizierung wird mit Nachricht „Erledigt“ beendet'
description: '* Adobe Commerce auf Cloud-Infrastruktur (alle Versionen)'
exl-id: 36ed9c9f-8280-41db-9df3-fe842dade4b1
feature: Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Adobe Commerce Cloud: Neuindizierung wird mit `Killed` Nachricht beendet

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur (alle Versionen)

## Problem

Sie versuchen, eine Neuindizierung auf der Integrationsverzweigung (oder im Staging des Starter-Architekturprojekts) auszuführen, und der Prozess wird mit der `Killed`-Meldung beendet.

## Ursache

Dies geschieht normalerweise, weil den PHP-Prozessen der Speicher ausgeht.
Der häufigste Grund ist eine große Anzahl von Produkten, Geschäften und/oder Kundengruppen in der Instanz.

## Lösung

1. Reduzieren Sie die Anzahl der Produkte (sowie ggf. Kundengruppen und Geschäfte).
1. Verwendung auf einen oder zwei gleichzeitige Benutzer beschränken.
1. Deaktivieren Sie Cron-Aufträge und führen Sie sie nach Bedarf manuell aus.
1. Falls dies noch nicht geschehen ist, fordern Sie ein Upgrade für die erweiterten Integrationsumgebungen an - beachten Sie die Beschränkung der Anzahl der Umgebungen, auf die Sie nach dem Upgrade beschränkt wären. Weitere Informationen finden Sie [ Artikel „Anfrage zur Verbesserung der Integrationsumgebung - Pro und ](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md)&quot; in unserer Support-Wissensdatenbank.

## Verwandtes Lesen:

In unserer Entwicklerdokumentation:

* [Pro Architektur > Integrationsumgebung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Starterarchitektur > Staging-Umgebung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#cloud-arch-stage)
