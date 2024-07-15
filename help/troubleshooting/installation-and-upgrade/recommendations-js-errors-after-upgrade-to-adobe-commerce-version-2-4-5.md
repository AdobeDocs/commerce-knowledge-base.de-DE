---
title: '[!UICONTROL Recommendations] [!DNL JS] Fehler nach der Aktualisierung auf Adobe Commerce Version 2.4.5'
description: Dieser Artikel enthält eine Fehlerbehebung für Fälle, in denen nach der Aktualisierung auf Adobe Commerce (alle Bereitstellungsmethoden) in der Konsole  [!DNL JS] Fehler im Zusammenhang mit den Produkt-Modulen [!UICONTROL Recommendations] auftreten.
feature: Install, Upgrade
role: Developer
exl-id: 51d899eb-48f7-48c5-8bda-bd72a4d28945
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# [!UICONTROL Recommendations] [!DNL JS] Fehler nach der Aktualisierung auf Adobe Commerce Version 2.4.5

Dieser Artikel enthält eine Fehlerbehebung für Fälle, in denen nach der Aktualisierung auf Adobe Commerce (alle Bereitstellungsmethoden) in der Konsole [!DNL JS] Fehler im Zusammenhang mit den Produkt-Modulen/Einheiten [!UICONTROL Recommendations] aufgetreten sind.

Es gibt derzeit keine Pläne, dieses Problem in zukünftigen Versionen zu beheben.

## Betroffene Versionen und Produkte

* Adobe Commerce (alle Bereitstellungsmethoden) bei der Aktualisierung auf Version 2.4.5

## Problem

Das Problem wird durch die Storefront-Webseite verursacht, die immer noch auf einige gelöschte Produkt- [!UICONTROL Recommendations] -Module/Einheiten (Bausteine und/oder Widgets) auf ihrer Startseite [!DNL CMS] verweist.

<u>Zu reproduzierende Schritte</u>:

1. Upgrade auf Adobe Commerce 2.4.5.
1. Rufen Sie die Storefront-Webseite auf.
1. Klicken Sie mit der rechten Maustaste und wählen Sie **Inspect** aus, um den Webinspektor in Ihrem Webbrowser zu öffnen.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Console]** .
1. Überprüfen Sie die [!DNL JS] -Fehler.

<u>Erwartete Ergebnisse</u>:

Erfolgreiches Upgrade ohne [!DNL JS]-Fehler.

<u>Tatsächliche Ergebnisse</u>:

In der Webbrowser-Konsole werden verschiedene Typen von [!DNL JS] -Fehlern angezeigt.

## Workaround

Als Problemumgehung können Sie alle auf der Seite verwendeten [!UICONTROL Recommendations] Einheiten überprüfen und alle gelöschten Einheiten entfernen.
