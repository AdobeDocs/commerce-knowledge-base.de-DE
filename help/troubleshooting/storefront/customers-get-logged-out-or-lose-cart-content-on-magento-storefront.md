---
title: Kunden werden abgemeldet oder verlieren den Warenkorbinhalt in der Adobe Commerce-Storefront
description: Dieser Artikel bietet eine Lösung und Problemumgehung für das Problem, bei dem Kundinnen und Kunden abgemeldet werden oder Artikel aus dem Warenkorb in der Storefront verlieren, nachdem sie von Zahlungsdiensten oder anderen Drittanbieterdiensten zurück zum Adobe Commerce-Store weitergeleitet wurden (Sitzungs-Cookie geht verloren).
exl-id: 9175570c-b06c-4a65-b8ca-7a12ff266afb
feature: Orders, Page Content, Shopping Cart, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%
---
# Kunden werden abgemeldet oder verlieren den Warenkorbinhalt in der Adobe Commerce-Storefront

Dieser Artikel bietet eine Lösung für das Problem, bei dem Kundinnen und Kunden abgemeldet werden oder Artikel aus dem Warenkorb in der Storefront verlieren, nachdem sie von Zahlungsdiensten oder anderen Drittanbieterdiensten zurück zum Adobe Commerce-Store weitergeleitet wurden (Sitzungs-Cookie geht verloren).

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premise, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Adobe Commerce auf Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

<u>Schritte zur Reproduktion:</u>

1. Der Kunde fügt Produkte in den Warenkorb auf der Storefront ein und geht zur Kasse.
1. Der Kunde wird zur Zahlungs-/Versandseite oder zu anderen Informationen/Services an die Website eines Drittanbieters weitergeleitet.
1. Der Kunde wird zurück zum Geschäft weitergeleitet.

<u>Tatsächliches Ergebnis:</u>

Der Kunde wurde zum leeren Warenkorb oder zu einer leeren Seite weitergeleitet.

<u>Erwartetes Ergebnis:</u>

Der Kunde wurde zu einer Erfolgszahlungsseite (oder einer anderen Erfolgsseite) umgeleitet, ohne die Checkout-Daten und den Fortschritt zu verlieren.

## Ursache

Das SameSite-Cookie-Attribut ist auf *Lax* oder nicht angegeben (was als festgelegt behandelt wird *Lax* ). Mit `SameSite` = *Lax* wird die Übertragung eines Cookies an externe URLs über `POST` deaktiviert.

## Lösung

Um das Problem zu beheben, wenden Sie sich an den Drittanbieter und bitten Sie seine Entwickler, ihre Integrationen zu aktualisieren, um Cookie-Parameter zu konfigurieren.

## Verwandtes Lesen

[Chrome SameSite-Update](https://www.chromestatus.com/feature/5088147346030592)
