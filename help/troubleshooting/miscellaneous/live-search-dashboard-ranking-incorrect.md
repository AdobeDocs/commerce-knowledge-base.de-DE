---
title: '[!DNL Live Search] Dashboard- und Suchergebnisrang ist falsch'
description: In diesem Artikel finden Sie Informationen zur Fehlerbehebung, wenn die Daten im [!DNL Live Search] Dashboard falsch sind oder die Rangfolge der Suchergebnisse nicht Ihren Erwartungen entspricht.
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: d4aea1f1-c2c4-45e5-87c8-73069f7c9ffd
source-git-commit: 9bb839292a120a3dab5151d493f915619dbf5c06
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---

# [!DNL Live Search] Dashboard- und Suchergebnisrang ist falsch

Wenn Sie feststellen, dass die im Dashboard [!DNL Live Search] angezeigten Daten nicht korrekt sind oder dass der [Rang der Suchergebnisse](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/category-merch#ranking-strategies) nicht Ihren Erwartungen entspricht, sehen Sie aus möglichen Gründen Folgendes:

* Das Feld `topLevelSku` des Produktkontexts in `productView` -Ereignissen fehlt. Dies führt zu leeren Konversionen und anderen unerwarteten Metriken.

* Für das `add-to-cart`-Ereignis ist das Feld `productContext` nicht festgelegt und ausgefüllt.

* Der Umgebungstyp ist falsch. Wenn die Umgebung beispielsweise auf *[!UICONTROL Testing]* anstelle von *[!UICONTROL Production]* festgelegt ist. Weitere Informationen finden Sie unter [Storefront context](https://github.com/adobe/commerce-events/blob/main/examples/events/example-contexts/mock-storefront-context.md) .

* Der Suchergebniskontext fehlt im [search-product-click](https://github.com/adobe/commerce-events/blob/main/examples/events/search-product-click.md) -Ereignis.
