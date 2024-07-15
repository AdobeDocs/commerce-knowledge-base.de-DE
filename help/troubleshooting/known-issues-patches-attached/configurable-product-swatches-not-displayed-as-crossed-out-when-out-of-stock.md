---
title: Konfigurierbare Produktmuster, die nicht angezeigt werden, sind nicht vorrätig
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.2.2-Problem, das sich auf die konfigurierbaren Produktmuster bezieht, die nicht vorrätig sind und auf der Storefront als überkreuzt angezeigt werden.
exl-id: 79c59a3f-a94b-4726-8af1-5fe754ea95a5
feature: Configuration, Orders, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Konfigurierbare Produktmuster, die nicht angezeigt werden, sind nicht vorrätig

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.2.2-Problem, das sich auf die konfigurierbaren Produktmuster bezieht, die nicht vorrätig sind und auf der Storefront als überkreuzt angezeigt werden.

## Problem

Wenn Sie über ein konfigurierbares Produkt verfügen und für eine bestimmte Kombination von Optionen das zugehörige einfache Produkt nicht vorrätig ist, ist das Muster weiterhin verfügbar und kann auf der Storefront ausgewählt werden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie in Commerce Admin ein konfigurierbares Produkt mit Optionen für zwei Attribute: Farbe (rot, schwarz) und Größe (S, M, L).
1. Legen Sie für jedes entsprechende einfache Produkt &quot;1&quot;fest.
1. Fügen Sie in der Storefront ein rotes Produkt vom Typ M zum Warenkorb und zum Checkout hinzu.
1. Verarbeiten Sie die Bestellung im Admin so, dass die Artikelmenge auf &quot;0&quot;aktualisiert wird.
1. Stellen Sie sicher, dass Rückstände nicht zulässig sind.
1. Navigieren Sie in der Storefront zur selben Produktseite und wählen Sie dieselben Optionen aus: Rot, M.

<u>Erwartete Ergebnisse</u>:

Das rote M-Muster hat einen roten Schrägstrich und kann nicht ausgewählt werden.

<u>Tatsächliche Ergebnisse</u>:

Das rote M-Muster kann ausgewählt werden.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-8215\_EE\_2.2.2\_v1.composer.patch herunterladen](assets/MDVA-8215_EE_2.2.2_v1.composer.patch.zip)

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce (alle Bereitstellungsmethoden) 2.2.2

Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce vor Ort und Adobe Commerce über Cloud-Infrastruktur 2.2.0-2.2.3

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches.

## Attached Files
