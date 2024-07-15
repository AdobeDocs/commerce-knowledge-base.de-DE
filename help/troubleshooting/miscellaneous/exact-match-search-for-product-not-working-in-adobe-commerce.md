---
title: Exakte Übereinstimmungssuche funktioniert in Adobe Commerce 2.4.x nicht
description: In diesem Artikel wird das Problem geklärt, dass die Suchergebnisse für die Vorderseite des Stores, die dieselbe Suchzeichenfolge verwenden, in Adobe Commerce 2.4.x im Vergleich zu Adobe Commerce 2.3.x unterschiedlich sind.
exl-id: 0867558e-1d74-4b83-abf3-651ca7fc32cb
feature: Products, Search
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Exakte Übereinstimmungssuche funktioniert in Adobe Commerce 2.4.x nicht

In diesem Artikel wird das Problem geklärt, dass die Suchergebnisse für die Vorderseite des Stores, die dieselbe Suchzeichenfolge verwenden, in Adobe Commerce 2.4.x im Vergleich zu Adobe Commerce 2.3.x unterschiedlich sind.

## Betroffene Produkte und Versionen

- Adobe Commerce (alle Bereitstellungsmethoden) 2.4.x, 2.3.x
- Live Search

## Problem

<u>Voraussetzungen:</u>

Sie haben Produkte mit den Attributwerten `Saga 1` und `Saga 16` sowohl in Adobe Commerce 2.3 als auch in Adobe Commerce 2.4 Stores.

<u>Zu reproduzierende Schritte:</u>

1. Geben Sie auf der Storefront eines Adobe Commerce 2.3-Stores *Saga 1* in das Suchfeld ein und klicken Sie auf **Suchen**.
1. Beachten Sie, dass Sie in den Suchergebnissen nur die Produkte mit dem Attributwert `Saga 1` erhalten.
1. Geben Sie auf der Storefront eines Adobe Commerce 2.4-Stores *Saga 1* in das Suchfeld ein und klicken Sie auf **Suchen**.

<u>Tatsächliches Ergebnis:</u>

Die Suchergebnisse in 2.4 umfassen Produkte mit den Attributwerten `Saga 1` und `Saga 16`.

<u>Erwartetes Ergebnis:</u>

Die Suchergebnisse in 2.4 ähneln 2.3 und enthalten nur Produkte mit dem Attributwert `Saga 1`.

## Ursache

Die native Adobe Commerce-Suchfunktion, die in 2.3.x verwendet wird, liefert exakte Suchergebnisse. Während die Live-Suche, ein optionales, für die Installation verfügbares Modul, das mit Adobe Commerce 2.4.x veröffentlicht wurde, unterschiedlich implementiert ist, ist das tatsächliche Ergebnis das erwartete Verhalten bei der Verwendung des Moduls.

## Verwandte Informationen

[Installieren Sie die Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) in unserem Benutzerhandbuch.

[Live Search](https://devdocs.magento.com/live-search/overview.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=Live%20Search) in unserer Entwicklerdokumentation.
