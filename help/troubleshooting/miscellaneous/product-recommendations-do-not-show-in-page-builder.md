---
title: Produkt-Recommendations wird nicht im Seitenaufbau angezeigt
description: Dieser Artikel bietet eine Lösung für das Problem, bei dem die Option Produkt-Recommendations nicht im Seitenaufbau angezeigt wird.
exl-id: e96a446b-2e64-47a6-ac1b-e73183da9fb8
feature: Page Builder, Configuration, Personalization, Products, Recommendations
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Produkt-Recommendations wird nicht im Seitenaufbau angezeigt

Dieser Artikel bietet eine Lösung für das Problem, bei dem die Option Produkt-Recommendations nicht im Seitenaufbau angezeigt wird.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden)

## Problem

Die Option &quot;Produkt-Recommendations&quot;wird nicht im Seitenaufbau angezeigt.

## Ursache

Im Seitenaufbau gibt es keine Option, Produkt-Recommendations hinzuzufügen. Product Recommendations for Page Builder ist ein optionales Modul und wird separat installiert.

## Lösung

1. Überprüfen Sie, ob Sie das Modul separat installiert haben, indem Sie den Befehl ausführen: `composer show magento/module-page-builder-product-recommendations`
1. Wenn die folgende Meldung zurückgegeben wird: *Paketmagento/module-page-builder-product-recommendations not found*, müssen Sie sie installieren, indem Sie den Befehl `composer require magento/module-page-builder-product-recommendations` ausführen:

Durch die Aktivierung von Product Recommendations in Page Builder können Sie jedem in Page Builder erstellten Inhalt [eine Empfehlungseinheit ](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) hinzufügen.

## Verwandtes Lesen

* [Inhalt hinzufügen - Produkt-Recommendations](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) in unserem Benutzerhandbuch.
* [Installieren und Konfigurieren von Product Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure) in unserer Entwicklerdokumentation.
* [Adobe Commerce-Benutzerhandbuch](https://experienceleague.adobe.com/en/docs/commerce-admin/user-guides/home)
