---
title: Site im Wartungsmodus, aber für Kunden verfügbar
description: Dieser Artikel enthält eine Korrektur für den Fall, dass der Wartungsmodus aktiviert ist (ein Adobe Commerce zum Problem mit der Cloud-Infrastruktur), aber die Storefront für Kunden weiterhin verfügbar ist.
exl-id: 61b81fbd-a382-44b5-94e9-5b6d72f11349
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Site im Wartungsmodus, aber für Kunden verfügbar

Dieser Artikel enthält eine Korrektur für den Fall, dass der Wartungsmodus aktiviert ist (ein Adobe Commerce zum Problem mit der Cloud-Infrastruktur), aber die Storefront für Kunden weiterhin verfügbar ist.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur (alle Versionen)

## Problem

<u>Zu reproduzierende Schritte:</u>

1. Aktivieren Sie den Wartungsmodus für die Site.
1. Navigieren Sie zur Storefront.

<u>Erwartetes Ergebnis:</u>

Die Wartungsseite wird angezeigt.

<u>Tatsächliches Ergebnis:</u>

Storefront-Seiten werden wie gewohnt angezeigt.

## Ursache

Seiten werden weiterhin zwischengespeichert, sodass die Wartungsseite nicht angezeigt wird.

## Lösung für die Site, die trotz des Wartungsmodus sichtbar ist

1. SSH in Ihrer Umgebung.
1. Führen Sie den Befehl `php bin/magento cache:clean` aus.

## Verwandtes Lesen

[Aktivieren oder deaktivieren Sie den Wartungsmodus](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-maint.html) in unserer Entwicklerdokumentation.
