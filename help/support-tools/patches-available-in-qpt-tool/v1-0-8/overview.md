---
title: '"Übersicht: [!DNL Quality Patches Tool] (QPT) v1.0.8'''
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.0.8.
exl-id: 6cd3eabe-067f-4e80-b17f-561290499261
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.8 - Übersicht

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.0.8.

QPT v1.0.8 enthält die folgenden Patches:

1. **MDVA-28357**: Ersetzt den Standard-Analyzer durch einen benutzerdefinierten Analyzer durch den Keyword-Tokenizer für das SKU-Feld im [!DNL ElasticSearch] Index , damit Platzhaltersuchabfragen mit SKUs funktionieren, die einen Bindestrich enthalten (&quot;-&quot;).
1. **MDVA-29954**: Behebt das Problem, bei dem der *Neue Anforderung zur Unternehmensregistrierung* und *Sie wurden mit einer Firma verbunden* E-Mails werden von der falschen Adresse gesendet.
1. **MDVA-30112**: Behebung des Problems, bei dem die Anzahl der Bestellungen die Variable *Bounch-Größe* -Wert, berücksichtigt Adobe Commerce die Bestellungen mit *pending* Status als Inkonsistenzen.
1. **MDVA-30963**: Behebung des Problems, bei dem die Ergebnisse der Produktfilterung so eingestellt sind, dass sie nur die für *Alle Store-Ansichten* im Admin-Bereich Produkte mit Werten einschließen, die auf der Ebene der Store-Ansicht überschrieben werden.
1. **MDVA-31150**: Behebung des Problems, bei dem die Guthaben- und Geschenkkarten-Storekonten nicht vom GET Invoice Rest API-Aufruf zurückgegeben wurden, wenn die Rechnung per REST API-Aufruf gepostet wurde und die Bestellung teilweise von Kredit- und Geschenkkartenkonten beglichen wurde.
1. **MDVA-31242**: Behebung des Problems, bei dem ein falsches Währungszeichen in angezeigt wurde. [!UICONTROL Credit Memo] Gitter.
1. **MDVA-31295**: Behebung des Problems, bei dem die Belohnungspunkte nicht berechnet werden, wenn eine partielle Bestellung abgeschlossen und Artikel besteuert werden.

Navigieren Sie über das Menü links zu einer bestimmten Patch-Seite.
