---
title: Site im Wartungsmodus, aber für Kunden verfügbar
description: Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass der Wartungsmodus aktiviert ist (ein Problem mit Adobe Commerce in der Cloud-Infrastruktur), die Storefront jedoch weiterhin für Kunden verfügbar ist.
exl-id: 61b81fbd-a382-44b5-94e9-5b6d72f11349
feature: Cache
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%
---
# Site im Wartungsmodus, aber für Kunden verfügbar

Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass der Wartungsmodus aktiviert ist (ein Problem mit Adobe Commerce in der Cloud-Infrastruktur), die Storefront jedoch weiterhin für Kunden verfügbar ist.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur (alle Versionen)

## Problem

<u>Schritte zur Reproduktion:</u>

1. Aktivieren Sie den Wartungsmodus für die Site.
1. Navigieren Sie zur Storefront.

<u>Erwartetes Ergebnis:</u>

Die Wartungsseite wird angezeigt.

<u>Tatsächliches Ergebnis:</u>

Storefront-Seiten werden wie gewohnt angezeigt.

## Ursache

Seiten werden weiterhin zwischengespeichert, sodass die Wartungsseite nicht angezeigt wird.

## Lösung für Standort trotz Wartungsmodus sichtbar

1. SSH in Ihre Umgebung.
1. Führen Sie den `php bin/magento cache:clean` Befehl aus.

## Verwandtes Lesen

[Wartungsmodus aktivieren oder deaktivieren](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in unserer Entwicklerdokumentation.
