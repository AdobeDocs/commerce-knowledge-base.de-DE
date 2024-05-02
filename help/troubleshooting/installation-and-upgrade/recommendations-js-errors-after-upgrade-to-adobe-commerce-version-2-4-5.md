---
title: '[!UICONTROL Recommendations] [!DNL JS] Fehler nach der Aktualisierung auf Adobe Commerce Version 2.4.5'
description: Dieser Artikel enthält eine Fehlerbehebung, wenn nach der Aktualisierung auf Adobe Commerce (alle Bereitstellungsmethoden) [!DNL JS] Fehler in der Konsole im Zusammenhang mit dem Produkt [!UICONTROL Recommendations] Module.
feature: Install, Upgrade
role: Developer
exl-id: 51d899eb-48f7-48c5-8bda-bd72a4d28945
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# [!UICONTROL Recommendations] [!DNL JS] Fehler nach der Aktualisierung auf Adobe Commerce Version 2.4.5

Dieser Artikel enthält eine Fehlerbehebung, wenn nach der Aktualisierung auf Adobe Commerce (alle Bereitstellungsmethoden) [!DNL JS] Fehler in der Konsole im Zusammenhang mit dem Produkt [!UICONTROL Recommendations] Module/Einheiten.

Es gibt derzeit keine Pläne, dieses Problem in zukünftigen Versionen zu beheben.

## Betroffene Versionen und Produkte

* Adobe Commerce (alle Bereitstellungsmethoden) bei der Aktualisierung auf Version 2.4.5

## Problem

Das Problem wird durch die Storefront-Webseite verursacht, die immer noch auf ein gelöschtes Produkt verweist. [!UICONTROL Recommendations] Module/Einheiten (Blöcke und/oder Widgets) auf der Startseite [!DNL CMS].

<u>Zu reproduzierende Schritte</u>:

1. Upgrade auf Adobe Commerce 2.4.5.
1. Rufen Sie die Storefront-Webseite auf.
1. Klicken Sie mit der rechten Maustaste auf die Maus und wählen Sie **Inspect** , um den Webinspektor in Ihrem Webbrowser zu öffnen.
1. Klicken Sie auf **[!UICONTROL Console]** Registerkarte.
1. Überprüfen Sie die [!DNL JS] Fehler.

<u>Erwartete Ergebnisse</u>:

Erfolgreiches Upgrade ohne [!DNL JS] Fehler.

<u>Tatsächliche Ergebnisse</u>:

Verschiedene Typen [!DNL JS] -Fehler in der Webbrowser-Konsole angezeigt.

## Workaround

Als Problemumgehung können Sie alle [!UICONTROL Recommendations] -Einheiten, die Sie auf der Seite verwendet haben, und entfernen Sie alle gelöschten Einheiten.
