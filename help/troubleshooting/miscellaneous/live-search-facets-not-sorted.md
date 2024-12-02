---
title: '[!DNL Live Search] Facetten sind nicht alphabetisch sortiert'
description: Dieser Artikel enthält Informationen zur Fehlerbehebung, wenn die [!DNL Live Search] Facetten nicht alphabetisch sortiert sind.
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

Adobe Commerce-Versionen 2.4.x und neuer

## Problem

Alle Adobe Commerce Storefront-Facetten werden alphabetisch mit Einzelauswahl-Optionen sortiert, unabhängig vom Eingabetyp, der dem entsprechenden Attribut zugewiesen ist.

## Workaround

In bestimmten Sonderfällen werden Facetten jedoch möglicherweise nicht alphabetisch sortiert, wie im Arbeitsbereich [[!DNL Live Search] Faceting](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/facets/faceting-workspace) eingerichtet.

Als Problemumgehung können Sie Produktattribute im Abschnitt [!UICONTROL Admin] -Attribute sortieren.

1. Wechseln Sie in der Seitenleiste **[!UICONTROL Admin]** zu **Stores** > *Attribute* > **Produkt**.
1. Wählen Sie ein Attribut aus der Tabelle aus.

   ![Attributliste](assets/attribute-list.png)

1. Öffnen Sie das Attribut mit den Werten, die Sie sortieren möchten, und wählen Sie **Attributinformationen** > **Eigenschaften** aus.
1. Unter **Optionen verwalten** können Sie die Attributwerte sortieren.

   ![Sortierattribute](assets/sort-attributes.png)
