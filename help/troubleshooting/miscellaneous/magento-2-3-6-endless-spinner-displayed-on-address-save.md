---
title: "Adobe Commerce 2.3.6: beim Speichern der Adresse angezeigter endloser Spinner"
description: In diesem Artikel wird ein bekanntes Problem mit Adobe Commerce 2.3.6 beschrieben, bei dem der Wartewirt unbegrenzt angezeigt wird, wenn eine Adresse in Mein Konto auf der Storefront gespeichert wird.
exl-id: 63841114-167e-4915-b6ed-ee0ef4eae36e
feature: Shipping/Delivery, Orders, Checkout
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Adobe Commerce 2.3.6: Auf Adressspeicherung angezeigter endloser Spinner

In diesem Artikel wird ein bekanntes Problem mit Adobe Commerce 2.3.6 beschrieben, bei dem der Wartewirt unbegrenzt angezeigt wird, wenn eine Adresse in Mein Konto auf der Storefront gespeichert wird.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.3.6 mit aktivierter Vertex-Integration (nur Firefox-Browser)

## Problem

Beim Speichern einer Adresse im Abschnitt Mein Konto auf der Storefront wird manchmal der Wartewirt aufgrund eines Fehlers in Vertex Core JS unbegrenzt angezeigt.

## Workaround

Problemumgehung: Verwenden Sie einen alternativen Browser zu Firefox.

Das Problem wurde in Adobe Commerce 2.3.1 behoben.

## Verwandtes Lesen

* [Verschiedene Adressen, die bei der Aufhebung der Auswahl von &quot;Meine Abrechnungs- und Lieferadresse sind identisch&quot;nicht zulässig sind, werden mit der VertexAddress-Bereinigung verwendet](/help/troubleshooting/miscellaneous/vertex-address-cleansing-different-addresses-not-allowed.md) in unserer Wissensdatenbank.
* [Adobe Commerce 2.4.1 Validierungsmeldung für Reklame-Adressen nach der Aktualisierung der Adresse](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md) in unserer Wissensdatenbank.
