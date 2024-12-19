---
title: Tausende von Ergebnissen bei der Suche nach einem bestimmten Produkt
description: Dieser Artikel bietet eine Lösung für das Problem, dass Sie Tausende von Suchergebnissen erhalten, wenn Sie nach einem bestimmten Produkt suchen.
feature: Quotes, Search, Returns
role: Developer, Admin
exl-id: 0eccf212-96be-4ea5-9e6e-95f27d7d9f92
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Tausende von Ergebnissen bei der Suche nach einem bestimmten Produkt

Dieser Artikel bietet eine Lösung für das Problem, dass Sie Tausende von Suchergebnissen erhalten, wenn Sie nach einem bestimmten Produkt suchen.

## Betroffene Produkte und Versionen

* Adobe Commerce - alle Versionen mit installiertem [!DNL ElasticSearch]

## Probleme

Sie suchen nach einem bestimmten Produkt (z. B. *WSH12-32-Red*), aber die Suche gibt viele ähnliche Produkte zurück.

## Lösungen

Die Art einer Volltextsuche in [!DNL ElasticSearch] basiert auf der Relevanz, nicht auf einer exakten Übereinstimmung. Daher werden die meisten relevanten Übereinstimmungen (wie exakt übereinstimmende SKU) zuerst bestellt.

Wenn Sie jedoch ein Suchergebnis benötigen, das genau mit Ihrem Suchbegriff übereinstimmt (exakte Übereinstimmung), sollten Sie für Ihre Suchanfrage Anführungszeichen verwenden. Beispielsweise gibt die Abfrage für *WSH12-32-Red* ohne Anführungszeichen mehrere Ergebnisse zurück, wobei die exakte Übereinstimmung (Produkt mit *SKU WSH12-32-Red*) im Ergebnis zuerst angezeigt wird. Die angegebene Abfrage *„WSH12-32-Red“* gibt jedoch nur ein exaktes Übereinstimmungsergebnis zurück.
