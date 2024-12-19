---
title: '[!DNL Live Search] Dashboard und das Suchergebnis-Ranking sind falsch'
description: Dieser Artikel enthält Informationen zur Fehlerbehebung, wenn die Daten im  [!DNL Live Search] -Dashboard falsch sind oder wenn das Ranking der Suchergebnisse nicht das ist, was Sie erwarten.
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: d4aea1f1-c2c4-45e5-87c8-73069f7c9ffd
source-git-commit: 9bb839292a120a3dab5151d493f915619dbf5c06
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---

# [!DNL Live Search] Dashboard und das Suchergebnis-Ranking sind falsch

Wenn Sie bemerken, dass die im [!DNL Live Search]-Dashboard angezeigten Daten falsch sind oder wenn das [Ranking der Suchergebnisse](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/category-merch#ranking-strategies) nicht das ist, was Sie erwarten, sehen Sie sich Folgendes aus möglichen Gründen an:

* Das `topLevelSku` Feld des Produktkontexts in `productView` Ereignissen fehlt. Dies führt zu leeren Konversionen und anderen unerwarteten Metriken.

* Für das `add-to-cart`-Ereignis ist das Feld `productContext` nicht festgelegt und ausgefüllt.

* Der Umgebungstyp ist falsch. Wenn die Umgebung beispielsweise auf *[!UICONTROL Testing]* statt auf *[!UICONTROL Production]* festgelegt ist. Siehe [Storefront-Kontext](https://github.com/adobe/commerce-events/blob/main/examples/events/example-contexts/mock-storefront-context.md) für weitere Informationen.

* Der Suchergebniskontext fehlt im Ereignis [search-product-click](https://github.com/adobe/commerce-events/blob/main/examples/events/search-product-click.md).
