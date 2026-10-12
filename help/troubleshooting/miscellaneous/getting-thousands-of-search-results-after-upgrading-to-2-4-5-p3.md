---
title: Tausende von Ergebnissen bei der Suche nach einem bestimmten Produkt
description: Dieser Artikel bietet eine Lösung für das Problem, dass Sie Tausende von Suchergebnissen erhalten, wenn Sie nach einem bestimmten Produkt suchen.
feature: Quotes, Search, Returns
role: Developer, Admin
exl-id: 0eccf212-96be-4ea5-9e6e-95f27d7d9f92
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 792a7e9b-6519-5e99-a913-56c3dd2408da
    internal-label: Quotes
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '190'
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
