---
title: '[!DNL Live Search] Facetten sind nicht alphabetisch sortiert'
description: Dieser Artikel enthält Informationen zur Fehlerbehebung, wenn die [!DNL Live Search] nicht alphabetisch sortiert sind.
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: 59f86727-c2a6-4418-8753-40f7937e059c
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
source-wordcount: '146'
ht-degree: 0%
---
# [!DNL Live Search] Facetten sind nicht alphabetisch sortiert

## Betroffene Produkte und Versionen

Adobe Commerce-Versionen 2.4.x und höher

## Problem

Alle Facetten der Adobe Commerce-Storefront werden alphabetisch mit Einzelauswahloptionen sortiert, unabhängig vom Eingabetyp, der dem entsprechenden Attribut zugewiesen ist.

## Abhilfe

In bestimmten Randfällen werden Facetten jedoch möglicherweise nicht alphabetisch sortiert, wie dies im Arbeitsbereich [[!DNL Live Search] Facettierung“ ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/facets/faceting-workspace) wurde.

Als Problemumgehung können Sie Produktattribute im Abschnitt [!UICONTROL Admin] sortieren.

1. Navigieren Sie in der **[!UICONTROL Admin]** Seitenleiste zu **Stores** > *Attribute* > **Product**.
1. Wählen Sie ein Attribut aus der Tabelle aus.

   ![Attributliste](assets/attribute-list.png)

1. Öffnen Sie das Attribut mit den Werten, die Sie sortieren möchten, und wählen Sie **Attributinformationen** > **Eigenschaften**.
1. Unter **Optionen verwalten** können Sie die Attributwerte sortieren.

   ![Attribute sortieren](assets/sort-attributes.png)
