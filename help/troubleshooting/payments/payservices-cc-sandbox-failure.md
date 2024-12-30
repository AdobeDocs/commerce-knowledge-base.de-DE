---
title: Fehlgeschlagene Kreditkartenzahlungen in einer Sandbox-Umgebung
description: In diesem Artikel wird erläutert, warum ein Test mit einer Kreditkarte in einer Sandbox-Umgebung mit PayPal-APIs fehlschlägt.
exl-id: 65fd08e0-eefc-47f3-8964-bef3610e6182
feature: Orders, Payments
role: Developer
source-git-commit: 958067830d32b1f10ffa669307ec76d1e14b82a4
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Fehlgeschlagene Kreditkartenzahlungen in einer Sandbox-Umgebung

In diesem Artikel wird erläutert, warum ein Test mit einer Kreditkarte in einer Sandbox-Umgebung mit PayPal-APIs fehlschlägt.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.0 - 2.4.4 , alle Bereitstellungsoptionen, mit [Payment Services](https://marketplace.magento.com/magento-payment-services.html)

## Problem

Bei der Verwendung einer Test-Visa-Kreditkarte `4111 1111 1111 1111` von PayPal schlägt sie manchmal aufgrund von PayPal-Betrugsrichtlinien mit dem folgenden Fehler fehl:

```bash
Error happened when processing the request. Please try again later.
```

## Ursache

Dieser Fehler wird angezeigt, wenn PayPal eine bestimmte Test-Kreditkartennummer für Betrug kennzeichnet. Dies geschieht, weil es sich um eine Test-Kreditkartennummer handelt, die von allen auf der ganzen Welt verwendet wird, um mit PayPal-APIs zu testen.

## Lösung

Benutze eine andere Test-Kreditkarte. Um Pseudo-Kreditkarten zu generieren, können Sie für Tests verwenden:

1. Rufen Sie die Seite PayPal Developer Portal [Kreditkartengenerator](https://developer.paypal.com/api/rest/sandbox/card-testing/#link-creditcardgenerator) auf.
1. Melden Sie sich beim PayPal-Entwicklerportal-Dashboard an.
1. Erstellen Sie eine Test-Kreditkarte.
