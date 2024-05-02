---
title: "Bekanntes Problem bei Adobe Commerce 2.3.7-p1: veraltete Bestellsumme für PayPal"
description: "Dieser Artikel enthält einen Patch für ein bekanntes Problem in Adobe Commerce 2.3.7-p1: Wenn Sie PayPal Checkout verwenden, erhalten Kunden das zuvor bestellte Produkt mehr als einmal im Warenkorb, anstatt das neue Produkt zu bestellen."
exl-id: ceb8f7ad-0cf7-4d42-aded-25d1dd947f5b
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Bekanntes Problem in Adobe Commerce 2.3.7-p1: veraltete Bestellsumme für PayPal

Dieser Artikel enthält einen Patch für ein bekanntes Problem in Adobe Commerce 2.3.7-p1: Wenn Sie PayPal Checkout mehr als einmal verwenden, erhalten Kunden das zuvor bestellte Produkt im Warenkorb, anstatt das neue Produkt, das sie versuchen zu bestellen.
Sie können den Patch von diesem Artikel herunterladen und er ist auch über das Quality Patches Tool (QPT) verfügbar.

## Betroffene Versionen

* Adobe Commerce (alle Bereitstellungsoptionen) 2.3.7-p1
* Magento Open Source 2.3.7-p1

## Problem

Wenn Sie eine Bestellung mit der Zahlungsmethode PayPal Express Checkout aufgeben, wird das zuvor bestellte Produkt in die Bestellung aufgenommen und nicht die eigentliche.

<u>Zu reproduzierende Schritte:</u>

1. Fügen Sie auf der Storefront ein Produkt zum Warenkorb hinzu (Produkt A, Preis 50 USD).
1. Klicken Sie auf den Link Warenkorb , um den Warenkorb zu öffnen.
1. Klicken Sie auf **PayPal Checkout** Schaltfläche.
1. Verwenden Sie Ihre PayPal-Anmeldedaten, um sich bei PayPal anzumelden und die Zahlung abzuschicken.
1. Beenden Sie die Bestellplatzierung auf der Store-Seite.
1. Gehen Sie zurück zum Katalog und fügen Sie dem Warenkorb ein anderes Produkt hinzu (Produkt B, Preis 100 USD).
1. Klicken Sie auf den Link Warenkorb , um den Warenkorb zu öffnen.
1. Klicken Sie auf **PayPal Checkout** Schaltfläche.

<u>Ergebnis:</u>

Der Produktpreis im Warenkorb beträgt 50 USD anstelle von 100 USD.<br/>
Auf der Seite des Stores enthält die Bestellung Produkt A anstelle von Produkt B.

<u>Erwartetes Ergebnis:</u>

Produkt B wird der Bestellung hinzugefügt.

## Lösung

Wenden Sie den in diesem Artikel bereitgestellten Patch an.

## Patch

Verwenden Sie den folgenden Link, um eine ZIP-Datei mit dem Patch herunterzuladen: [MC42674-Composer.patch.zip](assets/MC42674-composer.patch.zip).

### Kompatible Adobe Commerce-Versionen

* Adobe Commerce (alle Bereitstellungsoptionen) 2.3.7-p1

## Anwenden der Patches

1. Entpacken Sie die heruntergeladene ZIP-Datei.
1. Siehe [Anwenden eines von Adobe bereitgestellten Composer-Patches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) für weitere Anweisungen.
