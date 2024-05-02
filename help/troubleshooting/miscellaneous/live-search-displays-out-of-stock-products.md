---
title: '''[!DNL Live Search] zeigt nicht vorrätige Produkte unabhängig von den Einstellungen für den Lagerstatus in der Admin-Konsole an.'
description: Dieser Artikel enthält Informationen zum bekannten Problem, bei dem die Produktlistungsseite (Product Listing Page, PLP) das Symbol *Wir können keine Produkte finden, die mit dem selection*-Fehler übereinstimmen, während das Such-Popup einige Elemente zurückgibt.
exl-id: 2a351b83-407c-444a-a761-4932b5b88843
feature: Admin Workspace, Categories, Orders, Products, Search
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# [!DNL Live Search] zeigt nicht vorrätige Produkte unabhängig von den Einstellungen für den Lagerstatus in der Admin-Konsole an

>[!IMPORTANT]
>
>Dieses Problem wurde in [[!DNL Live Search] [2.0.4]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html). Informationen zum Installieren der neuesten Version finden Sie unter [Aktualisieren [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#update) im Benutzerhandbuch.

Dieser Artikel enthält Informationen zum bekannten Problem, bei dem die Produktlistungsseite (Product Listing Page, PLP) die *Wir können keine Produkte finden, die der Auswahl entsprechen* -Fehler angezeigt, während das Such-Popup einige Elemente zurückgibt.

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.x

## Problem

[!DNL Live Search] zeigt Suchergebnisse unabhängig von den Einstellungen für den Lagerstatus im Adobe Commerce Admin an. Auch wenn die **[!UICONTROL Display Out-of-Stock Products]** auf *Nein*, werden die Produkte angezeigt. Dies führt zum PLP-Fehler. *Wir können keine Produkte finden, die der Auswahl entsprechen*.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Kategorie und fügen Sie Produkte hinzu. (Beispiel: Kategorie = _Jeans_, Product1 = _Blue Jeans_, Product2 = _Schwarze Jeans_)
1. Alle Produkte der Kategorie sind nicht mehr vorrätig.
1. Satz **[!UICONTROL Display Out-of-Stock Products]** nach *Nein*.
1. Geben Sie in die Storefront ein. *Jeans* im Suchfeld.
1. Klicks **[!UICONTROL View All]** im Popup-Fenster angezeigt.

<u>Erwartetes Ergebnis</u>:

Sie sehen die *Wir können keine Produkte finden, die der Auswahl entsprechen* auf PLP angezeigt werden und keine Produkte im Popup-Fenster &quot;Suche&quot;angezeigt werden.

<u>Tatsächliches Ergebnis</u>:

Sie sehen die *Wir können keine Produkte finden, die der Auswahl entsprechen* auf PLP angezeigt und beide Produkte werden im Such-Popup angezeigt.

## Lösung

Es gibt derzeit keine Lösung für dieses Problem. Unsere [!DNL Live Search] Team wird in Kürze eine Einstellung zur Konfiguration [!DNL Live Search] , um Produkte korrekt anzuzeigen.

## Verwandtes Lesen

[Installieren [!DNL Live Search]](https://docs.magento.com/user-guide/live-search/install.html) in unserem Benutzerhandbuch.
