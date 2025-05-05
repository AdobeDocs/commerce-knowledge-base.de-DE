---
title: Die Suche nach exakten Übereinstimmungen funktioniert in Adobe Commerce 2.4.x nicht
description: Dieser Artikel bietet eine Klarstellung für das Problem, dass die Suchergebnisse für die Storefront, die dieselbe Suchzeichenfolge verwenden, in Adobe Commerce 2.4.x im Vergleich zu Adobe Commerce 2.3.x unterschiedlich sind.
exl-id: 0867558e-1d74-4b83-abf3-651ca7fc32cb
feature: Products, Search
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Die Suche nach exakten Übereinstimmungen funktioniert in Adobe Commerce 2.4.x nicht

Dieser Artikel bietet eine Klarstellung für das Problem, dass die Suchergebnisse für die Storefront, die dieselbe Suchzeichenfolge verwenden, in Adobe Commerce 2.4.x im Vergleich zu Adobe Commerce 2.3.x unterschiedlich sind.

## Betroffene Produkte und Versionen

- Adobe Commerce (alle Bereitstellungsmethoden) 2.4.x, 2.3.x
- Live Search

## Problem

<u>Voraussetzungen:</u>

Es befinden sich Produkte mit den Attributwerten `Saga 1` und `Saga 16` sowohl in Adobe Commerce 2.3- als auch in Adobe Commerce 2.4-Stores.

<u>Schritte zur Reproduktion:</u>

1. Geben Sie an der Storefront eines mit Adobe Commerce 2.3 ausgestatteten Stores *Saga 1* in das Suchfeld ein und klicken Sie auf **Suchen**.
1. Beachten Sie, dass Sie in den Suchergebnissen nur die Produkte mit dem Attributwert `Saga 1` erhalten.
1. Geben Sie an der Storefront eines mit Adobe Commerce 2.4 betriebenen Stores *Saga 1* in das Suchfeld ein und klicken Sie auf **Suche**.

<u>Tatsächliches Ergebnis:</u>

Die Suchergebnisse in 2.4 enthalten Produkte mit den Attributwerten `Saga 1` und `Saga 16`.

<u>Erwartetes Ergebnis:</u>

Die Suchergebnisse in 2.4 ähneln 2.3 und umfassen nur Produkte mit dem Attributwert `Saga 1`.

## Ursache

Die in 2.3.x verwendete native Adobe Commerce-Suchfunktion liefert exakte Suchergebnisse für Übereinstimmungen. Während Live Search, ein optionales Modul, das für die Installation verfügbar ist und mit Adobe Commerce 2.4.x veröffentlicht wurde, anders implementiert wird, ist das tatsächliche Ergebnis das erwartete Verhalten, wenn das Modul verwendet wird.

## Verwandtes Lesen

[Live Search installieren](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=de) in unserem Benutzerhandbuch.

[Live Search](https://experienceleague.adobe.com/de/docs/commerce-merchant-services/live-search/overview) in unserer Entwicklerdokumentation.
