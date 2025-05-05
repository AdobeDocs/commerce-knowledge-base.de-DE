---
title: Installieren der neuesten Patches zur Behebung von Adobe Commerce Redis-Problemen
description: Dieser Artikel enthält Informationen zu den neuesten Redis-bezogenen Patches, die im Paket [Adobe Commerce on Cloud Infrastructure Patches](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) verfügbar sind.
exl-id: 0335bc11-f679-4629-b4e7-6a0e68c3ae44
feature: Cache, Install, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Installieren der neuesten Patches zur Behebung von Adobe Commerce Redis-Problemen

Dieser Artikel enthält Informationen zu den neuesten Redis-bezogenen Patches, die im Paket [Adobe Commerce on Cloud Infrastructure Patches](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) verfügbar sind.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur 2.3.3, 2.3.4

## Problem

Ein zusätzlicher CPU- und Speicherverbrauch von Redis kann die Adobe Commerce-Leistung und damit die Gesamtleistung Ihrer Website verringern.

## Lösung

Wenden Sie die neuesten von Adobe Commerce bereitgestellten Patches auf das Cloud-Infrastruktur-Patchpaket an. Detaillierte Anweisungen finden Sie unter [Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

Die neuesten Redis-Patches, die von Adobe Commerce für das Cloud-Infrastruktur-Patchpaket bereitgestellt werden, tragen zu Folgendem bei:

* Reduzierung der Netzwerkkommunikation für Redis
* Beheben von Racebedingungen, die zu zusätzlichem Speicherverbrauch führen
* Ändern des Cache-Adapters zur Abdeckung von Zwangsräumungsfällen
* Verringern des Verbrauchs von Redis CPU

Adobe Commerce empfiehlt auch ein Upgrade auf Redis 5, wenn Sie Adobe Commerce auf Cloud-Infrastruktur 2.3.3 oder höher ausführen.
