---
title: Produktempfehlungen werden in Page Builder nicht angezeigt
description: Dieser Artikel bietet eine Lösung für den Fall, dass die Option Produktempfehlungen in Page Builder nicht angezeigt wird.
exl-id: e96a446b-2e64-47a6-ac1b-e73183da9fb8
feature: Page Builder, Configuration, Personalization, Products, Recommendations
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Produktempfehlungen werden in Page Builder nicht angezeigt

Dieser Artikel bietet eine Lösung für den Fall, dass die Option Produktempfehlungen in Page Builder nicht angezeigt wird.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden)

## Problem

Option „Produktempfehlungen“ wird in Page Builder nicht angezeigt.

## Ursache

In Page Builder gibt es keine Option zum Hinzufügen von Produktempfehlungen. Product Recommendations für Page Builder ist ein optionales Modul und wird separat installiert.

## Lösung

1. Überprüfen Sie, ob Sie das Modul separat installiert haben, indem Sie den folgenden Befehl ausführen: `composer show magento/module-page-builder-product-recommendations`
1. Wenn die Meldung zurückgegeben wird: *Package magento/module-page-builder-product-recommendations not found*, müssen Sie sie durch Ausführen des Befehls installieren: `composer require magento/module-page-builder-product-recommendations`

Durch die Aktivierung von Produktempfehlungen in Page Builder können Sie [ in Page Builder erstellten Inhalten ](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html)eine Empfehlungseinheit hinzufügen“.

## Verwandtes Lesen

* [Inhalt hinzufügen - Produktempfehlungen](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) in unserem Benutzerhandbuch.
* [Installieren und Konfigurieren von Produktempfehlungen](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure) finden Sie in unserer Entwicklerdokumentation.
* [Adobe Commerce-Benutzerhandbuch](https://experienceleague.adobe.com/en/docs/commerce-admin/user-guides/home)
