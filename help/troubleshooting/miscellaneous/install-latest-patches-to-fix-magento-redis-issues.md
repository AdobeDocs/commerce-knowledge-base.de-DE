---
title: Installieren Sie die neuesten Patches, um Probleme mit Adobe Commerce Redis zu beheben
description: Dieser Artikel enthält Informationen zu den neuesten Redis-bezogenen Patches, die im Paket [Adobe Commerce on Cloud Infrastructure Patches](https://devdocs.magento.com/cloud/project/project-patch.html) verfügbar sind.
exl-id: 0335bc11-f679-4629-b4e7-6a0e68c3ae44
feature: Cache, Install, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Installieren Sie die neuesten Patches, um Probleme mit Adobe Commerce Redis zu beheben

Dieser Artikel enthält Informationen zu den neuesten Redis-bezogenen Patches, die in [Adobe Commerce auf Cloud-Infrastrukturpatches](https://devdocs.magento.com/cloud/project/project-patch.html) Paket.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur 2.3.3, 2.3.4

## Problem

Ein zusätzlicher CPU- und Speicherverbrauch von Redis kann die Leistung von Adobe Commerce und damit die Gesamtleistung Ihrer Website beeinträchtigen.

## Lösung

Wenden Sie die neuesten Patches an, die von Adobe Commerce im Cloud-Infrastruktur-Patches-Paket bereitgestellt werden. Detaillierte Anweisungen finden Sie unter [Anwenden von Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

Die neuesten Redis-Patches, die von Adobe Commerce im Cloud-Infrastruktur-Patches-Paket bereitgestellt werden, tragen zu Folgendem bei:

* Reduzierung der Netzwerkkommunikation für Redis
* Reparieren von Wettlaufsituationen, die zu einem zusätzlichen Speicherverbrauch führen
* Ändern des Cache-Adapters zur Abdeckung von Ausscheidungsfällen
* Verringern des CPU-Verbrauchs von Redis

Adobe Commerce empfiehlt auch ein Upgrade auf Redis 5, wenn Sie Adobe Commerce auf Cloud-Infrastruktur 2.3.3 oder höher ausführen.
