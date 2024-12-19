---
title: Site im Wartungsmodus, aber für Kunden verfügbar
description: Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass der Wartungsmodus aktiviert ist (ein Problem mit Adobe Commerce in der Cloud-Infrastruktur), die Storefront jedoch weiterhin für Kunden verfügbar ist.
exl-id: 61b81fbd-a382-44b5-94e9-5b6d72f11349
feature: Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '149'
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

[Wartungsmodus aktivieren oder deaktivieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in unserer Entwicklerdokumentation.
