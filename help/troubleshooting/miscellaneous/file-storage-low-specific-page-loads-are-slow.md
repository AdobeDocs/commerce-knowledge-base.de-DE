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

Geringer Festplattenspeicher und langsame Seitenladevorgänge können durch große, umfassende Bilder verursacht werden, die in `pub/media/catalog/products` hohe Speichermengen verwenden und Speicherplatz zwischen Staging und Produktion freigeben (es sei denn, es wird eine dedizierte Staging-Umgebung bereitgestellt).

## Ursache

Bilder werden nicht optimiert, um die Leistung mit der Anzeigequalität in Einklang zu bringen.

## Lösung

Optimieren und komprimieren Sie sie vor dem Hochladen von Bildern, um die Leistung mit der Anzeigequalität in Einklang zu bringen. Dadurch wird der Speicherplatz erhöht und die Seitenladezeiten verkürzt. PNGs bieten kleinere Bildgrößen mit großen einfarbigen Bereichen. JPEG geben kleinere Größen für alles andere an. Verwenden Sie die höchste Komprimierung (ohne spürbaren Abbau). Dies beträgt in der Regel 60-80 %.

Verwenden Sie [Fastly image optimization](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html), um speichereffizientere Bilder zu erzeugen.

## Verwandtes Lesen

Weitere Informationen zum Verwalten des Festplattenspeichers (wenn Sie sich in Adobe Commerce in der Cloud-Infrastruktur befinden) finden Sie unter [Verwalten des Festplattenspeichers in Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) im Commerce on Cloud Infrastructure Guide.
