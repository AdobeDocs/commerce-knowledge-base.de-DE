---
title: 'Bekanntes Problem in Adobe Commerce 2.4.0: fehlende Kennzeichnung „Rückerstattung“ in Klarna'
description: Dieser Artikel bietet eine Problemumgehung für ein bekanntes Problem in Admin wegen eines fehlenden **Refund**-Labels in Klarna VBE (Vendor Bundled Extension). Bei der Durchführung einer Rückerstattung im Klarna-Portal wird das **Refund**-Label nicht neben dem zurückerstatteten Paket-Produkt angezeigt.
exl-id: f08039b2-7f8b-481e-8ec8-1659e227744f
feature: B2B, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%
---
# Bekanntes Problem in Adobe Commerce 2.4.0: fehlende Kennzeichnung „Rückerstattung“ in Klarna

Dieser Artikel bietet eine Problemumgehung für ein bekanntes Problem in Admin wegen eines fehlenden **Refund**-Labels in Klarna VBE (Vendor Bundled Extension). Bei der Durchführung einer Rückerstattung im Klarna-Portal wird das **Rückerstattung**-Label nicht neben dem zurückerstatteten Paket-Produkt angezeigt.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.4.0
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

## Problem

<u>Voraussetzungen:</u>

* Klarna ist aktiviert.
* Ein gebündeltes Produkt wird erstellt.

<u>Schritte zur Reproduktion</u>

1. Wechseln Sie zum Adobe Commerce-Frontend und fügen Sie ein gebündeltes Produkt zum **hinzu**.
1. Navigieren Sie zur Kasse.
1. Geben Sie Verbraucherinformationen in die Kasse ein und klicken Sie auf **Weiter**.
1. Wählen Sie **KP-Option** und klicken Sie auf **Bestellung aufgeben**.
1. Wechseln Sie **Admin** > **Verkauf** > **Bestellungen**.
1. Öffnen Sie die Bestellung.
1. Rechnung für das Produkt erstellen.
1. Wechseln Sie zu **Rechnungen** > **Rechnung auswählen** > Klicken Sie auf **Gutschrift** > Klicken Sie auf **Rückerstattung** (nicht **Rückerstattung offline**).
1. Zum Klarna-Portal.
1. Öffnen Sie die Bestellung.
1. Das **Refund**-Label ist vorhanden.

<u>Erwartetes Ergebnis</u>

Auf dem Klarna-Portal **neben dem** Produkt das Label „Rückerstattung“ angezeigt.

<u>Tatsächliches Ergebnis</u>

Auf dem Klarna-Portal **das** „Rückerstattung“ nicht neben dem zurückerstatteten Produkt angezeigt.

## Abhilfe

Die Problemumgehung besteht darin, das fehlende **Refund**-Label im Klarna-Portal für zurückerstattete gebündelte Produkte zu ignorieren. Die Rückerstattung ist erfolgt, obwohl das **Rückerstattung**-Label nicht angezeigt wurde. Das Problem wird voraussichtlich in Adobe Commerce 2.4.1 behoben, das im 4. Quartal 2020 veröffentlicht werden soll.

## Weiterführende Informationen finden Sie in unserer Support-Wissensdatenbank:

* [Adobe Commerce 2.4.0 Bekanntes Problem: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Fehlermeldung bei Auswahl der lokalen Zahlungsmethode, die für einige Länder während des Checkouts angezeigt wird](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
