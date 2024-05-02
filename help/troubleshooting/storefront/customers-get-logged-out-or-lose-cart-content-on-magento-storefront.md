---
title: Kunden werden abgemeldet oder verlieren den Warenkorbinhalt in der Adobe Commerce-Storefront
description: Dieser Artikel bietet eine Lösung und eine Problemumgehung, bei der Kunden abgemeldet werden oder Artikel aus dem Warenkorb auf der Storefront verlieren, nachdem sie von Zahlungsdiensten oder anderen Drittanbieterdiensten an den Adobe Commerce-Store zurückgeleitet wurden (Sitzungs-Cookie "geht verloren").
exl-id: 9175570c-b06c-4a65-b8ca-7a12ff266afb
feature: Orders, Page Content, Shopping Cart, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# Kunden werden abgemeldet oder verlieren den Warenkorbinhalt in der Adobe Commerce-Storefront

Dieser Artikel bietet eine Lösung für das Problem, bei dem Kunden vom Warenkorb auf der Storefront abgemeldet werden oder Artikel verlieren, nachdem sie von einer Zahlung oder anderen Drittanbieterdiensten an den Adobe Commerce-Store zurückgeleitet wurden (Sitzungs-Cookie &quot;geht verloren&quot;).

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Adobe Commerce zur Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

<u>Zu reproduzierende Schritte:</u>

1. Der Kunde fügt Produkte in den Warenkorb der Storefront ein und fährt mit dem Checkout fort.
1. Der Kunde wird zur Bezahlung/Versand oder zu anderen Informationen/Dienstleistungen auf die Drittanbieter-Website weitergeleitet.
1. Der Kunde wird zurück zum Geschäft weitergeleitet.

<u>Ergebnis:</u>

Der Kunde wurde zum leeren Warenkorb oder zu einer leeren Seite umgeleitet.

<u>Erwartetes Ergebnis:</u>

Der Kunde wurde auf eine Erfolgszahlungsseite (oder eine andere Erfolgsseite) umgeleitet, ohne die Kassendaten und den Fortschritt zu verlieren.

## Ursache

Das SameSite-Cookie-Attribut ist auf *Lax* oder nicht spezifiziert (behandelt als *Lax* ). nach `SameSite` = *Lax* Deaktiviert die Übertragung eines Cookies über `POST` -Anfragen.

## Lösung

Um das Problem zu beheben, wenden Sie sich an den Drittanbieter und bitten Sie seine Entwickler, ihre Integrationen zu aktualisieren, um Cookie-Parameter zu konfigurieren.

## Verwandtes Lesen

[Chrome SameSite-Aktualisierung](https://www.chromestatus.com/feature/5088147346030592)
