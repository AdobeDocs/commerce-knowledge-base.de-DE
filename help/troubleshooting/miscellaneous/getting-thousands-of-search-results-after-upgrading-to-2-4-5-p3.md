---
title: Abrufen Tausender von Ergebnissen bei der Suche nach einem bestimmten Produkt
description: Dieser Artikel bietet eine Lösung für das Problem, dass Sie Tausende von Suchergebnissen erhalten, wenn Sie nach einem bestimmten Produkt suchen.
feature: Quotes, Search, Returns
role: Developer, Admin
exl-id: 0eccf212-96be-4ea5-9e6e-95f27d7d9f92
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Abrufen Tausender von Ergebnissen bei der Suche nach einem bestimmten Produkt

Dieser Artikel bietet eine Lösung für das Problem, dass Sie Tausende von Suchergebnissen erhalten, wenn Sie nach einem bestimmten Produkt suchen.

## Betroffene Produkte und Versionen

* Alle Versionen von Adobe Commerce mit [!DNL ElasticSearch] installiert

## Probleme

Sie suchen nach einem bestimmten Produkt (z. B. *WSH12-32-Red*), aber die Suche gibt viele ähnliche Produkte zurück.

## Lösungen

Die Art einer Volltextsuche in [!DNL ElasticSearch] basiert auf Relevanz, nicht auf exakter Übereinstimmung. Die meisten relevanten Übereinstimmungen (wie exakt übereinstimmende SKU) werden also zuerst bestellt.

Wenn Sie jedoch ein Suchergebnis benötigen, das genau mit Ihrem Suchbegriff übereinstimmt (genaue Übereinstimmung), sollten Sie Anführungszeichen für Ihre Suchabfrage verwenden. Beispiel: Abfrage für *WSH12-32-Red* ohne Anführungszeichen gibt mehrere Ergebnisse mit der exakten Übereinstimmung zurück (Produkt mit *SKU WSH12-32-Red*), das zuerst im Ergebnis erscheint. Aber zitierte Abfrage *&quot;WSH12-32-Red&quot;* gibt nur ein genaues Übereinstimmungsergebnis zurück.
