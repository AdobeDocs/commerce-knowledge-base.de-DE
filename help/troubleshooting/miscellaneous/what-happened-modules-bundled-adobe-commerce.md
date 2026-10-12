---
title: Module fehlen in Adobe Commerce 2.4.4
description: Dieser Artikel bietet eine Lösung für das Problem, wenn in früheren Adobe Commerce-Versionen enthaltene Module in 2.4.4 nicht vorhanden sind.
exl-id: c0335b66-803b-44d7-b966-7d60a5f21d8d
feature: Extensions
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: f08fa0de-a550-4acd-b570-f81cf1d03aaf
    internal-label: Commerce ecosystem
subfeature_v2:
  - id: dad884f1-e840-49a1-970e-2f965bdbc410
    internal-label: Extensions
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%
---
# Module fehlen in Adobe Commerce 2.4.4

Dieser Artikel bietet eine Lösung für Fälle, in denen in früheren Adobe Commerce-Versionen enthaltene Module in 2.4.4 nicht vorhanden sind.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden) - alle [unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problem

Sie können kein Modul eines Drittanbieters installieren oder haben festgestellt, dass einige der gebündelten Kernerweiterungen beim Upgrade auf Adobe Commerce 2.4.4 nicht vorhanden sind. Dies sollte nur durch die Installation eines Drittanbietermoduls erfolgen, für das eine der gebündelten Erweiterungen aus Adobe Commerce 2.4.4 entfernt werden muss, oder wenn das Projekt einige der Funktionen eines der entfernten Module nutzt.

* Szenario 1: Das Projekt hat eine der Funktionen des gebündelten Kernmoduls genutzt. Das verwendete Bundle-Modul ist nicht in Adobe Commerce 2.4.4 enthalten. Nach dem erfolgreichen Upgrade auf Adobe Commerce 2.4.4 stellen Sie fest, dass das -Modul und die bereitgestellte Funktionalität fehlen.

* Szenario 2: Sie haben ein Modul in Ihrem aktuellen Projekt installiert, das eine Abhängigkeit von einem der entfernten gebündelten Module aufweist.

Dieses Verhalten ist zu erwarten, da die vom Anbieter gebündelten Erweiterungen aus der Code-Basis von Adobe Commerce 2.4.4 entfernt wurden.

## Lösung

Installieren/kaufen Sie die offiziellen Erweiterungen separat. Diese sind auf der [Commerce Marketplace &#x200B;](https://marketplace.magento.com/extensions.html).

## Verwandtes Lesen

[Herstellerspezifische Erweiterungen](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-4.html?lang=de&#vendor-bundled-extensions) finden Sie in der Dokumentation zu Adobe Commerce > Versionsinformationen > Versionshinweise zu Adobe Commerce 2.4.4.
