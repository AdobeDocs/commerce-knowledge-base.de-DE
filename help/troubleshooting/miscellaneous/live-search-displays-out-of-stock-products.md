---
title: '[!DNL Live Search] zeigt nicht vorrätige Produkte an, unabhängig von den Einstellungen für den Lagerstatus in der Admin-Konsole.'
description: Dieser Artikel enthält Informationen zum bekannten Problem, bei dem die Produktlistungsseite (Product Listing Page, PLP) das Symbol *Wir können keine Produkte finden, die mit dem selection*-Fehler übereinstimmen, während das Such-Popup einige Elemente zurückgibt.
exl-id: 2a351b83-407c-444a-a761-4932b5b88843
feature: Admin Workspace, Categories, Orders, Products, Search
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# [!DNL Live Search] zeigt nicht vorrätige Produkte an, unabhängig von den Einstellungen für den Lagerstatus in der Admin-Konsole

>[!IMPORTANT]
>
>Dieses Problem wurde in [[!DNL Live Search] [2.0.4]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html) behoben. Informationen zum Installieren der neuesten Version finden Sie unter [Aktualisieren [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#update) im Benutzerhandbuch.

Dieser Artikel enthält Informationen zum bekannten Problem, bei dem die Produktlistungsseite (Product Listing Page, PLP) den Fehler &quot;*Wir können keine Produkte finden, die mit dem Fehler &quot;selection*&quot;übereinstimmen, während das Such-Popup einige Elemente zurückgibt.

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.x

## Problem

[!DNL Live Search] zeigt Suchergebnisse unabhängig von den Einstellungen für den Lagerstatus im Adobe Commerce Admin an. Selbst wenn **[!UICONTROL Display Out-of-Stock Products]** auf *Nein* gesetzt ist, werden die Produkte angezeigt. Dies führt zum PLP-Fehler *Wir können keine Produkte finden, die der Auswahl* entsprechen.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Kategorie und fügen Sie Produkte hinzu. (Beispiel: Kategorie = _Jeans_, Produkt1 = _Blue Jeans_, Produkt2 = _Black Jeans_)
1. Alle Produkte der Kategorie sind nicht mehr vorrätig.
1. Setzen Sie **[!UICONTROL Display Out-of-Stock Products]** auf *Nein*.
1. Geben Sie im Storefront *Jeans* in das Suchfeld ein.
1. Klicken Sie im Popup auf &quot;**[!UICONTROL View All]**&quot;.

<u>Erwartetes Ergebnis</u>:

Sie sehen die Meldung &quot;*Wir können keine Produkte finden, die mit der Auswahl-* -Meldung auf PLP übereinstimmen, und es werden keine Produkte im Such-Popup angezeigt.

<u>Tatsächliches Ergebnis</u>:

Sie sehen die Meldung &quot;*Wir können keine Produkte finden, die mit der Auswahl-* -Meldung auf PLP übereinstimmen, und beide Produkte werden im Such-Popup angezeigt.

## Lösung

Es gibt derzeit keine Lösung für dieses Problem. Unser [!DNL Live Search]-Team stellt in Kürze eine Einstellung bereit, mit der [!DNL Live Search] so konfiguriert werden kann, dass Produkte korrekt angezeigt werden.

## Verwandtes Lesen

[Installieren Sie [!DNL Live Search]](https://docs.magento.com/user-guide/live-search/install.html) in unserem Benutzerhandbuch.
