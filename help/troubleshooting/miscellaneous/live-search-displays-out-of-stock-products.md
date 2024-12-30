---
title: '[!DNL Live Search] zeigt nicht vorrätige Produkte unabhängig von den Lagerstatuseinstellungen in Admin an'
description: Dieser Artikel enthält Informationen zum bekannten Problem, bei dem auf der Produktlistenseite (PLP) der Fehler *Wir können Produkte, die der Auswahl entsprechen, nicht finden* angezeigt wird, während das Such-Pop-up einige Elemente zurückgibt.
exl-id: 2a351b83-407c-444a-a761-4932b5b88843
feature: Admin Workspace, Categories, Orders, Products, Search
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# [!DNL Live Search] zeigt nicht vorrätige Produkte unabhängig von den Lagerstatuseinstellungen in Admin an

>[!IMPORTANT]
>
>Dieses Problem wurde in [[!DNL Live Search] [2.0.4]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html) behoben. Informationen zur Installation der neuesten Version finden Sie [Aktualisieren [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#update) im Benutzerhandbuch.

Dieser Artikel enthält Informationen zum bekannten Problem, bei dem auf der Produktlistenseite (PLP) der Fehler *Wir können keine Produkte finden, die der Auswahl entsprechen* angezeigt wird, während das Such-Popover einige Elemente zurückgibt.

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.x

## Problem

[!DNL Live Search] zeigt Suchergebnisse unabhängig von den Stock-Statuseinstellungen in Adobe Commerce Admin an. Auch wenn die **[!UICONTROL Display Out-of-Stock Products]** auf &quot;*&quot;* ist, werden die Produkte angezeigt. Dies führt zum PLP-Fehler *Wir können keine Produkte finden, die der Auswahl entsprechen*.

<u>Schritte zur Reproduktion</u>:

1. Erstellen einer Kategorie, Hinzufügen von Produkten. (Beispiel: Kategorie = _Jeans_, Produkt1 = _Blue Jeans_, Produkt2 = _Black Jeans_)
1. Machen Sie alle Produkte in der Kategorie ausverkauft.
1. Setzen Sie **[!UICONTROL Display Out-of-Stock Products]** auf *Nein*.
1. Geben Sie in der Storefront *Suchfeld &quot;*&quot; ein.
1. Klicken Sie im Popup-Fenster auf **[!UICONTROL View All]** .

<u>Erwartetes Ergebnis</u>:

Die Meldung *Wir können keine Produkte finden, die der Auswahl entsprechen* wird auf PLP angezeigt, und im Such-Popup werden keine Produkte angezeigt.

<u>Tatsächliches </u>:

Die Meldung *Wir können keine Produkte finden, die der Auswahl entsprechen* wird auf PLP angezeigt. Beide Produkte werden im Suchfenster angezeigt.

## Lösung

Für dieses Problem gibt es derzeit keine Lösung. Unser [!DNL Live Search]-Team wird bald eine Einstellung bereitstellen, um [!DNL Live Search] so zu konfigurieren, dass Produkte korrekt angezeigt werden.

## Verwandtes Lesen

[Installieren [!DNL Live Search]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install) in unserer Anleitung.
