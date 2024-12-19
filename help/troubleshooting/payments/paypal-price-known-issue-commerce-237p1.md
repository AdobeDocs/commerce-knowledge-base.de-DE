---
title: 'Adobe Commerce 2.3.7-p1 Bekanntes Problem: Veraltete Bestellsumme für PayPal'
description: 'Dieser Artikel enthält einen Patch für ein bekanntes Problem in Adobe Commerce 2.3.7-p1: Wenn Sie PayPal Checkout mehr als einmal verwenden, erhalten Kundinnen und Kunden das zuvor bestellte Produkt in den Warenkorb anstatt des neuen, das sie zu bestellen versuchen.'
exl-id: ceb8f7ad-0cf7-4d42-aded-25d1dd947f5b
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Adobe Commerce 2.3.7-p1 Bekanntes Problem: Veraltete Bestellsumme für PayPal

Dieser Artikel enthält einen Patch für ein bekanntes Problem in Adobe Commerce 2.3.7-p1: Wenn Sie PayPal Checkout mehr als einmal verwenden, erhalten Kundinnen und Kunden das zuvor bestellte Produkt in den Warenkorb anstatt des neuen, das sie zu bestellen versuchen.
Sie können den Patch aus diesem Artikel herunterladen. Er ist auch über das Quality Patches Tool (QPT) verfügbar.

## Betroffene Versionen

* Adobe Commerce (alle Bereitstellungsoptionen) 2.3.7-p1
* Magento Open Source 2.3.7-P1

## Problem

Wenn Sie eine Bestellung mit der Zahlungsmethode PayPal Express Checkout aufgeben, wird das zuvor bestellte gekaufte Produkt in die Bestellung anstelle des tatsächlichen Produkts eingefügt.

<u>Schritte zur Reproduktion:</u>

1. Fügen Sie auf der Ladenfront jedes Produkt zum Warenkorb hinzu (Produkt A, Preis 50 $).
1. Klicken Sie auf den Link Warenkorb , um den Warenkorb zu öffnen.
1. Klicken Sie auf die **PayPal Checkout** Schaltfläche.
1. Verwenden Sie Ihre PayPal-Anmeldedaten, um sich bei PayPal anzumelden und die Zahlung zu übermitteln.
1. Platzierung der Bestellung auf der Ladenseite beenden.
1. Gehen Sie zurück zum Katalog und fügen Sie ein anderes Produkt (Produkt B, Preis $100) zum Warenkorb hinzu.
1. Klicken Sie auf den Link Warenkorb , um den Warenkorb zu öffnen.
1. Klicken Sie auf die **PayPal Checkout** Schaltfläche.

<u>Tatsächliches Ergebnis:</u>

Der Produktpreis im Warenkorb beträgt $50 statt $100.<br/>
Auf der Ladenseite enthält die Bestellung Produkt A anstelle Produkt B.

<u>Erwartetes Ergebnis:</u>

Produkt B wird der Bestellung hinzugefügt.

## Lösung

Wenden Sie das in diesem Artikel vorgesehene Patch an.

## Fleck

Verwenden Sie den folgenden Link, um eine ZIP-Datei mit dem Patch herunterzuladen: [MC42674-composer.patch.zip](assets/MC42674-composer.patch.zip).

### Kompatible Adobe Commerce-Versionen

* Adobe Commerce (alle Bereitstellungsoptionen) 2.3.7-p1

## Anwenden der Patches

1. Entpacken Sie die heruntergeladene ZIP-Datei.
1. Weitere [ finden Sie unter „Anwenden eines Composer-Patches ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) Adobe&quot;.
