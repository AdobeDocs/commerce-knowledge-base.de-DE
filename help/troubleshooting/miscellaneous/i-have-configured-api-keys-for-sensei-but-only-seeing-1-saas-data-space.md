---
title: Nach der Konfiguration von Adobe AI-API-Schlüsseln werden nicht mehrere SaaS-Datenräume angezeigt
description: Dieser Artikel bietet eine Lösung für Probleme, bei denen nach der Konfiguration der API-Schlüssel für Adobe AI nur ein SaaS-Datenspeicher angezeigt wird.
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
source-git-commit: 61f5a526a0c36c91739103c0802bc9794a425f38
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# Nach der Konfiguration von Adobe AI-API-Schlüsseln werden nicht mehrere SaaS-Datenräume angezeigt

Nach dem Konfigurieren von API-Schlüsseln für einen Commerce-Service wie Adobe AI-Services (Produktempfehlungen oder Live-Suche) oder Payment Services für Adobe Commerce werden voraussichtlich mehrere SaaS-Datenräume im Commerce Services-Connector angezeigt. Je nach Produktberechtigung und Bereitstellungstyp zeigt der Connector nur einen SaaS-Datenspeicher an, was das erwartete Verhalten ist.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden): Alle Versionen
* Magento Open Source: alle Versionen
* Erweiterung oder Technologie (Fastly, New Relic usw.), Adobe AI (Produktempfehlungen/Live Search)

## Problem

Nach dem Konfigurieren der Adobe AI-API-Schlüssel zeigt das System nur einen SaaS-Datenspeicher an.

## Ursache

Die Anzahl der verfügbaren SaaS-Datenräume hängt von der Produktberechtigung ab, die mit dem Commerce-Konto verknüpft ist, und vom Typ des verwendeten Services.

## Lösung

Im Allgemeinen hängt die Anzahl der verfügbaren SaaS-Datenräume von der Commerce-Lizenz ab:

* Adobe Commerce: ein Produktionsdatenbereich und zwei Testdatenbereiche
* Magento Open Source: Ein Produktionsdatenbereich und keine Testdatenbereiche

Für Zahlungs-Services lautet das Standardverhalten:

* Payment Services auf Adobe Commerce (*Cloud oder On-Premise*) verfügt standardmäßig über drei Datenräume:
* Ein Produktionsdatenbereich
* Zwei Testdatenräume
* Payment Services auf Magento Open Source verfügt standardmäßig über einen Datenspeicher

Kunden, die mehrere Cloud-Projekte oder On-Premise-Installationen (*live/production*) besitzen, können auch zusätzliche Produktions- und Testdatenbereiche für jedes Projekt oder jede Instanz anfordern, indem sie eine Support-Anfrage senden.

Magento Open Source-Kunden, die Adobe Payment Services verwenden, können auch einen zusätzlichen Datenspeicher anfordern. Wenden Sie sich zur vorherigen Genehmigung an das Zahlungs-Team, bevor Sie eine Support-Anfrage einreichen, um einen Testdatenbereich hinzuzufügen.

>[!NOTE]
> * Verwenden Sie nicht denselben SaaS-Datenspeicher in mehreren Umgebungen gleichzeitig. Wenn ein Produktions- oder Testdatenspeicher in verschiedenen Umgebungen wiederverwendet wird, können Daten gemischt werden und eine Bereinigung erfordern.
> * Zahlungsdienste in Adobe Commerce (*Cloud/On-Premise*) verfügen standardmäßig über drei Datenräume.
> * Zahlungsdienste auf Magento Open Source verfügen standardmäßig über einen einzigen Datenspeicher.
> So fordern Sie zusätzliche Datenräume an:
> * Magento Open Source-Kunden, die Adobe Payment Services verwenden, können einen zusätzlichen Datenspeicher anfordern. Wenden Sie sich zur vorherigen Genehmigung an das Zahlungs-Team, bevor Sie eine Support-Anfrage einreichen, um einen Testdatenbereich zu erhalten.
> * Kunden, die mehrere Cloud-Projekte oder On-Premise-Installationen (*live/production*) besitzen, können auch zusätzliche Produktions- und Testdatenbereiche für jedes Projekt oder jede Instanz anfordern, indem sie eine Support-Anfrage senden.

## Verwandtes Lesen

[SaaS-Datenspeicherbereitstellung](https://experienceleague.adobe.com/de/docs/commerce/user-guides/integration-services/saas?lang=en#saas-data-space-provisioning)
