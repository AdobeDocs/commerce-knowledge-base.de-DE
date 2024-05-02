---
title: Geringer Dateispeicher, bestimmte Seitenladevorgänge sind langsam
description: Dieser Artikel bietet eine Lösung für das Problem des geringen Festplattenspeicherplatzes, der durch große, Rich-Bilder verursacht wird.
exl-id: 640c8f0d-f714-4cc1-a401-9264cfaf8e37
feature: Storage, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Geringer Dateispeicher, bestimmte Seitenladevorgänge sind langsam

Dieser Artikel bietet eine Lösung für das Problem des geringen Festplattenspeicherplatzes, der durch große, Rich-Bilder verursacht wird.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle unterstützten Versionen
* Adobe Commerce vor Ort, alle unterstützten Versionen
* Magento Open Source, alle unterstützten Versionen

## Problem

Geringer Speicherplatz und langsame Seitenladevorgänge können durch große, umfassende Rich-Bilder verursacht werden, die hohe Speichermengen in `pub/media/catalog/products` und die Freigabe von Speicherplatz zwischen Staging und Produktion (es sei denn, eine dedizierte Staging-Umgebung wird bereitgestellt).

## Ursache

Bilder werden nicht optimiert, um die Leistung mit der Anzeigequalität in Einklang zu bringen.

## Lösung

Optimieren und komprimieren Sie sie vor dem Hochladen von Bildern, um die Leistung mit der Anzeigequalität in Einklang zu bringen. Dadurch wird der Speicherplatz erhöht und die Seitenladezeiten verkürzt. PNGs bieten kleinere Bildgrößen mit großen einfarbigen Bereichen. JPEG geben kleinere Größen für alles andere an. Verwenden Sie die höchste Komprimierung (ohne spürbaren Abbau). Dies beträgt in der Regel 60-80 %.

Verwendung [Schnelle Bildoptimierung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html) zur Erstellung von speichereffizienteren Bildern.

## Verwandtes Lesen

Informationen zum Verwalten Ihres Festplattenspeichers (wenn Sie sich in Adobe Commerce in der Cloud-Infrastruktur befinden) finden Sie unter [Verwalten des Festplattenspeichers in Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) im Commerce on Cloud Infrastructure Guide.
