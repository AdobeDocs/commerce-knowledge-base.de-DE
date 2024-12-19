---
title: Der Dateispeicher ist niedrig, bestimmte Seitenladevorgänge sind langsam
description: Dieser Artikel bietet eine Lösung für das Problem des geringen Festplattenspeichers, der durch große, umfangreiche Bilder verursacht wird.
exl-id: 640c8f0d-f714-4cc1-a401-9264cfaf8e37
feature: Storage, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Der Dateispeicher ist niedrig, bestimmte Seitenladevorgänge sind langsam

Dieser Artikel bietet eine Lösung für das Problem des geringen Festplattenspeichers, der durch große, umfangreiche Bilder verursacht wird.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle unterstützten Versionen
* Adobe Commerce On-Premise, alle unterstützten Versionen
* Magento Open Source, alle unterstützten Versionen

## Problem

Geringer Festplattenspeicher und langsame Seitenladevorgänge können durch große, umfangreiche Bilder verursacht werden, die große Mengen an Speicher in `pub/media/catalog/products` verwenden, und durch die gemeinsame Nutzung von Festplattenspeicher zwischen Staging und Produktion (es sei denn, eine dedizierte Staging-Umgebung wird bereitgestellt).

## Ursache

Bilder sind nicht optimiert, um Leistung und Anzeigequalität in Einklang zu bringen.

## Lösung

Optimieren und komprimieren Sie Bilder vor dem Hochladen, um ein ausgewogenes Verhältnis zwischen Leistung und Anzeigequalität zu erzielen. Dies erhöht den Speicherplatz und reduziert die Seitenladezeiten. PNG-Dateien bieten kleinere Größen für Bilder mit großen einfarbigen Bereichen. JPEG geben für alles andere kleinere Größen. Verwenden Sie die höchste Komprimierung (ohne merkliche Beeinträchtigung). Das sind in der Regel 60-80%.

Verwenden Sie [Fastly Image Optimization](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html), um speichereffizientere Bilder zu erstellen.

## Verwandtes Lesen

Informationen zum Verwalten des Festplattenspeichers (wenn Sie sich in der Cloud-Infrastruktur von Adobe Commerce befinden) finden Sie unter [Verwalten des Festplattenspeichers in der Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) im Handbuch zu Commerce in der Cloud-Infrastruktur.
