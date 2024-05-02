---
title: Fehlgeschlagene Kreditkartenzahlungen in einer Sandbox-Umgebung
description: In diesem Artikel wird erläutert, warum eine Test-Kreditkarte in einer Sandbox-Umgebung mit PayPal-APIs fehlschlägt.
exl-id: 65fd08e0-eefc-47f3-8964-bef3610e6182
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Fehlgeschlagene Kreditkartenzahlungen in einer Sandbox-Umgebung

In diesem Artikel wird erläutert, warum eine Test-Kreditkarte in einer Sandbox-Umgebung mit PayPal-APIs fehlschlägt.

## Betroffene Produkte und Versionen


* Adobe Commerce 2.4.0 - 2.4.4 , alle Bereitstellungsoptionen mit [Zahlungsdienste](https://marketplace.magento.com/magento-payment-services.html)

## Problem

Bei Verwendung einer Visa-Testkarte `4111 1111 1111 1111` von PayPal, manchmal scheitert es aufgrund von PayPal Betrug Richtlinien mit dem folgenden Fehler:

```terminal
Error happened when processing the request. Please try again later.
```

## Ursache

Dieser Fehler wird angezeigt, wenn PayPal eine bestimmte Test-Kreditkartennummer für Betrug markiert. Dies geschieht, weil es sich um eine Test-Kreditkartennummer handelt, die von allen auf der Welt mit PayPal-APIs getestet wird.

## Lösung

Verwenden Sie eine andere Test-Kreditkarte. Zum Generieren von nachgeahmten Kreditkarten können Sie zum Testen verwenden:

1. Wechseln Sie zum PayPal Developer Portal [Kreditkartengenerator](https://developer.paypal.com/developer/creditCardGenerator/) Seite.
1. Melden Sie sich beim PayPal Developer Portal-Dashboard an.
1. Generieren Sie eine Test-Kreditkarte.
