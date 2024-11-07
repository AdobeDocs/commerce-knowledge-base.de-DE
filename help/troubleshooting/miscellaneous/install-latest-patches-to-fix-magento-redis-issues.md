---
title: Installieren Sie die neuesten Patches, um Probleme mit Adobe Commerce Redis zu beheben
description: Dieser Artikel enthält Informationen zu den neuesten Redis-bezogenen Patches, die im Paket [Adobe Commerce on Cloud Infrastructure Patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) verfügbar sind.
exl-id: 0335bc11-f679-4629-b4e7-6a0e68c3ae44
feature: Cache, Install, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Installieren Sie die neuesten Patches, um Probleme mit Adobe Commerce Redis zu beheben

Dieser Artikel enthält Informationen zu den neuesten Redis-bezogenen Patches, die in [Adobe Commerce im Cloud-Infrastruktur-Patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) -Paket verfügbar sind.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur 2.3.3, 2.3.4

## Problem

Ein zusätzlicher CPU- und Speicherverbrauch von Redis kann die Leistung von Adobe Commerce und damit die Gesamtleistung Ihrer Website beeinträchtigen.

## Lösung

Wenden Sie die neuesten Patches an, die von Adobe Commerce im Cloud-Infrastruktur-Patches-Paket bereitgestellt werden. Detaillierte Anweisungen finden Sie unter [Anwenden von Patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

Die neuesten Redis-Patches, die von Adobe Commerce im Cloud-Infrastruktur-Patches-Paket bereitgestellt werden, tragen zu Folgendem bei:

* Reduzierung der Netzwerkkommunikation für Redis
* Reparieren von Wettlaufsituationen, die zu einem zusätzlichen Speicherverbrauch führen
* Ändern des Cache-Adapters zur Abdeckung von Ausscheidungsfällen
* Verringern des CPU-Verbrauchs von Redis

Adobe Commerce empfiehlt auch ein Upgrade auf Redis 5, wenn Sie Adobe Commerce auf Cloud-Infrastruktur 2.3.3 oder höher ausführen.
