---
title: '[!DNL Live Search] Facetten sind nicht alphabetisch sortiert'
description: Dieser Artikel enthält Informationen zur Fehlerbehebung, wenn  [!DNL Live Search]  Facetten nicht alphabetisch sortiert sind.
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: 59f86727-c2a6-4418-8753-40f7937e059c
source-git-commit: 9bb839292a120a3dab5151d493f915619dbf5c06
workflow-type: tm+mt
source-wordcount: '130'
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
