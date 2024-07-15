---
title: 'Overview: [!DNL Quality Patches Tool] (QPT) v1.0.8'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool]  (QPT) v1.0.8 verfügbaren Patches behoben wurden.
exl-id: 6cd3eabe-067f-4e80-b17f-561290499261
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# Überblick über [!DNL Quality Patches Tool] (QPT) v1.0.8

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.0.8 verfügbaren Patches behoben wurden.

QPT v1.0.8 enthält die folgenden Patches:

1. **MDVA-28357**: Ersetzt den Standard-Analyzer durch einen benutzerdefinierten Analyzer mit Keyword-Tokenizer für das SKU-Feld im [!DNL ElasticSearch] -Index, damit Platzhaltersuchabfragen mit SKUs funktionieren, die einen Bindestrich (&quot;-&quot;) enthalten.
1. **MDVA-29954**: Behebung des Problems, bei dem die E-Mails *Neue Anforderung zur Unternehmensregistrierung* und *Sie wurden mit einer Firma verknüpft* von der falschen Adresse gesendet wurden.
1. **MDVA-30112**: Behebung des Problems, bei dem Adobe Commerce die Bestellungen mit dem Status *ausstehend* als Inkonsistenzen betrachtet, wenn die Anzahl der Bestellungen den Wert *bunch-size* überschreitet.
1. **MDVA-30963**: Behebung des Problems, bei dem Produkte, die Ergebnisse filtern, die so eingestellt sind, dass sie nur Werte enthalten, die für den Bereich *Alle Store-Ansichten* im Admin festgelegt sind, Produkte mit Werten einschließen, die auf der Store-Ansichtsebene überschrieben werden.
1. **MDVA-31150**: Behebung des Problems, bei dem die Guthaben- und Geschenkkarten-Storekonten nicht vom GET Invoice Rest API-Aufruf zurückgegeben werden, wenn die Rechnung durch den Rest-API-Aufruf gepostet wurde und die Bestellung teilweise von Kredit- und Geschenkkartenkonten bezahlt wurde.
1. **MDVA-31242**: Behebung des Problems, bei dem ein falsches Währungszeichen im Raster [!UICONTROL Credit Memo] angezeigt wird.
1. **MDVA-31295**: Behebung des Problems, bei dem die Punkte nicht berechnet werden, wenn eine partielle Bestellung abgeschlossen und Artikel besteuert werden.

Navigieren Sie über das Menü links zu einer bestimmten Patch-Seite.
