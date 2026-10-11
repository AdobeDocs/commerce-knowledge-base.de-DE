---
title: '[!DNL Live Search] Dashboard und das Suchergebnis-Ranking sind falsch'
description: Dieser Artikel enthält Informationen zur Fehlerbehebung, wenn die Daten im [!DNL Live Search]-Dashboard falsch sind oder wenn das Ranking der Suchergebnisse nicht das ist, was Sie erwarten.
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: d4aea1f1-c2c4-45e5-87c8-73069f7c9ffd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%
---
# [!DNL Live Search] Dashboard und das Suchergebnis-Ranking sind falsch

Wenn Sie bemerken, dass die im [!DNL Live Search]-Dashboard angezeigten Daten falsch sind oder wenn das [Ranking der Suchergebnisse](https://experienceleague.adobe.com/de/docs/commerce-merchant-services/live-search/live-search-admin/category-merch#ranking-strategies) nicht das ist, was Sie erwarten, sehen Sie sich Folgendes aus möglichen Gründen an:

* Das `topLevelSku` Feld des Produktkontexts in `productView` Ereignissen fehlt. Dies führt zu leeren Konversionen und anderen unerwarteten Metriken.

* Für das `add-to-cart`-Ereignis ist das Feld `productContext` nicht festgelegt und ausgefüllt.

* Der Umgebungstyp ist falsch. Wenn die Umgebung beispielsweise auf *[!UICONTROL Testing]* statt auf *[!UICONTROL Production]* festgelegt ist. Siehe [Storefront-Kontext](https://github.com/adobe/commerce-events/blob/main/examples/events/example-contexts/mock-storefront-context.md) für weitere Informationen.

* Der Suchergebniskontext fehlt im Ereignis [search-product-click](https://github.com/adobe/commerce-events/blob/main/examples/events/search-product-click.md).
