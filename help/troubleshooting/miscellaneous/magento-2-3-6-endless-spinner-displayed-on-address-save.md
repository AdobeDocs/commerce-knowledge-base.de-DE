---
title: 'Adobe Commerce 2.3.6: Endlosspinner wird beim Speichern der Adresse angezeigt'
description: In diesem Artikel wird ein bekanntes Adobe Commerce 2.3.6-Problem beschrieben, bei dem beim Speichern einer Adresse im Bereich Mein Konto in der Storefront auf unbestimmte Zeit der Spinner angezeigt wird.
exl-id: 63841114-167e-4915-b6ed-ee0ef4eae36e
feature: Shipping/Delivery, Orders, Checkout
role: Developer
source-git-commit: ce377064efabaf09d3856da7c6c5c742a9fdcc2f
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---

# Adobe Commerce 2.3.6: Endlosspinner wird beim Speichern der Adresse angezeigt

In diesem Artikel wird ein bekanntes Adobe Commerce 2.3.6-Problem beschrieben, bei dem beim Speichern einer Adresse im Bereich Mein Konto in der Storefront auf unbestimmte Zeit der Spinner angezeigt wird.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.3.6 mit aktivierter Vertex-Integration (nur Firefox-Browser)

## Problem

Beim Speichern einer Adresse im Abschnitt Mein Konto auf der Storefront wird manchmal der Spinner für die Wartezeit aufgrund eines Fehlers in Vertex Core JS auf unbestimmte Zeit angezeigt.

## Abhilfe

Problemumgehung: Verwenden Sie einen alternativen Browser zu Firefox.

Das Problem wurde in Adobe Commerce 2.3.1 behoben.

## Verwandtes Lesen

* [Adobe Commerce 2.4.1 Vertex-Adressvalidierungsmeldung nach &#x200B;](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md) Aktualisierung der Adresse in unserer Support-Wissensdatenbank.
