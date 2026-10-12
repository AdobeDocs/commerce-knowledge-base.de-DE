---
title: Adobe Commerce 2.4.0 Virtual Terminal-Seite in Braintree beschädigt
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.4.0-Problem, bei dem die Seite "Braintree Virtual Terminal“ nicht die richtigen Benutzeroberflächenelemente lädt, oder eine korrekte Fehlermeldung, wenn Braintree nicht konfiguriert ist.
exl-id: 1d4d762d-2ab3-4752-ad6d-1eb6a179917d
feature: Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%
---
# Adobe Commerce 2.4.0 Virtual Terminal-Seite in Braintree beschädigt

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.4.0-Problem, bei dem die Seite &quot;Braintree Virtual Terminal“ nicht die richtigen Benutzeroberflächenelemente lädt, oder eine korrekte Fehlermeldung, wenn Braintree nicht konfiguriert ist.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.4.0
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

## Problem

### Szenario 1: Braintree-Zahlungsmethode ist konfiguriert

<u>Schritte zur Reproduktion:</u>

Wechseln Sie in Commerce Admin zu **Verkauf** > **Braintree Virtual Terminal** . **&#x200B; **

<u>Erwartetes Ergebnis:</u>

Die Seite **Braintree Virtual Terminal** wird mit der richtigen Benutzeroberfläche geladen.

<u>Tatsächliches Ergebnis:</u>

Die Benutzeroberfläche der Seite **Braintree Virtual Terminal** ist fehlerhaft.

### Szenario 2: Braintree-Zahlungsmethode ist konfiguriert

<u>Schritte zur Reproduktion:</u>

Wechseln Sie in Commerce Admin zu **Verkauf** > **Braintree Virtual Terminal** . **&#x200B; **

<u>Erwartetes Ergebnis:</u>

Die Seite **Braintree Virtual Terminal** wird mit der richtigen Benutzeroberfläche geladen, und es wird eine Warnung angezeigt, die darauf hinweist, dass Braintree noch nicht konfiguriert ist.

<u>Tatsächliches Ergebnis:</u>

Die Benutzeroberfläche der Seite **Braintree Virtual Terminal** ist fehlerhaft und es wird keine Warnung angezeigt.

## Lösung

Wenden Sie das in diesem Artikel vorgesehene Patch an.

## Fleck

Der Patch ist diesem Artikel beigefügt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[BUNDLE-2670-composer.patch](assets/BUNDLE-2670-composer.patch.zip)

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde erstellt für:

* Adobe Commerce auf Cloud-Infrastruktur 2.4.0
* Adobe Commerce On-Premises 2.4.0

## Anbringen des Pflasters

Anweisungen [&#x200B; Sie unter „Anwenden eines von Adobe bereitgestellten Composer](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento)Patches .

## Angehängte Dateien
