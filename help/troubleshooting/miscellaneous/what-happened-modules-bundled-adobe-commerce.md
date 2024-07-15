---
title: Fehlende Module in Adobe Commerce 2.4.4
description: Dieser Artikel bietet eine Lösung für das Problem, wenn in früheren Adobe Commerce-Versionen enthaltene Module in Version 2.4.4 nicht vorhanden sind.
exl-id: c0335b66-803b-44d7-b966-7d60a5f21d8d
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Fehlende Module in Adobe Commerce 2.4.4

Dieser Artikel bietet eine Lösung für den Fall, dass in früheren Adobe Commerce-Versionen enthaltene Module in Version 2.4.4 nicht vorhanden sind.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden) alle [unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problem

Sie können kein Drittanbietermodul installieren oder festgestellt haben, dass einige der Kernerweiterungen bei der Aktualisierung auf Adobe Commerce 2.4.4 nicht vorhanden sind. Dies sollte sich nur aus der Installation eines Drittanbietermoduls ergeben, für das eine der gebündelten Erweiterungen aus Adobe Commerce 2.4.4 entfernt werden muss, oder wenn das Projekt einen Teil der Funktionalität eines der entfernten Module nutzt.

* Szenario 1: Das Projekt hat eine der Funktionen des Kernpakets verwendet. Das verwendete gebündelte Modul ist nicht in Adobe Commerce 2.4.4 enthalten. Nach der erfolgreichen Aktualisierung auf Adobe Commerce 2.4.4 ist Ihnen klar, dass das Modul und die bereitgestellten Funktionen fehlen.

* Szenario 2: Sie haben ein Modul in Ihrem aktuellen Projekt installiert, das von einem der entfernten gebündelten Module abhängig ist.

Dies ist ein erwartetes Verhalten, da die Vendor-Bundle-Erweiterungen aus der Codebasis von Adobe Commerce 2.4.4 entfernt wurden.

## Lösung

Installieren/erwerben Sie die offiziellen Erweiterungen separat. Diese sind auf der [Commerce Marketplace](https://marketplace.magento.com/extensions.html) verfügbar.

## Verwandtes Lesen

[Vendor-Bundle-Erweiterungen](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-4.html?#vendor-bundled-extensions) in der Adobe Commerce-Dokumentation > Versionsinformationen > Versionshinweise zu Adobe Commerce 2.4.4.
