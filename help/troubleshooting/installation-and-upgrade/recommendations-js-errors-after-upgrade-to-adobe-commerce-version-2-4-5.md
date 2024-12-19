---
title: '[!UICONTROL Recommendations] [!DNL JS] Fehler nach der Aktualisierung auf Adobe Commerce Version 2.4.5'
description: Dieser Artikel bietet eine Korrektur für den Fall, dass nach dem Upgrade auf Adobe Commerce (alle Bereitstellungsmethoden)  [!DNL JS]  Konsolenfehler im Zusammenhang mit den [!UICONTROL Recommendations] auftreten.
feature: Install, Upgrade
role: Developer
exl-id: 51d899eb-48f7-48c5-8bda-bd72a4d28945
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# [!UICONTROL Recommendations] [!DNL JS] nach der Aktualisierung auf Adobe Commerce Version 2.4.5

Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass nach dem Upgrade auf Adobe Commerce (alle Bereitstellungsmethoden) in der Konsole [!DNL JS] Fehler im Zusammenhang mit den Produktmodulen/-[!UICONTROL Recommendations] auftreten.

Es gibt derzeit keine Pläne, dieses Problem in zukünftigen Versionen zu beheben.

## Betroffene Versionen und Produkte

* Adobe Commerce (alle Bereitstellungsmethoden) beim Upgrade auf Version 2.4.5

## Problem

Das Problem wird dadurch verursacht, dass die Web-Seite der Storefront weiterhin auf einige gelöschte [!UICONTROL Recommendations] (Blöcke und/oder Widgets) auf ihrer Startseite [!DNL CMS] verweist.

<u>Schritte zur Reproduktion</u>:

1. Aktualisieren Sie auf Adobe Commerce 2.4.5.
1. Rufen Sie die Web-Seite der Storefront auf.
1. Klicken Sie mit der rechten Maustaste, und wählen Sie **Inspect**, um den Web-Inspektor in Ihrem Webbrowser zu öffnen.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Console]** .
1. Überprüfen Sie die [!DNL JS].

<u>Erwartete Ergebnisse</u>:

Erfolgreiches Upgrade ohne [!DNL JS].

<u>Tatsächliche Ergebnisse</u>:

In der Konsole des Webbrowsers werden verschiedene Arten von [!DNL JS] angezeigt.

## Abhilfe

Als Problemumgehung können Sie alle [!UICONTROL Recommendations] Einheiten überprüfen, die Sie auf der Seite verwendet haben, und gelöschte Einheiten entfernen.
