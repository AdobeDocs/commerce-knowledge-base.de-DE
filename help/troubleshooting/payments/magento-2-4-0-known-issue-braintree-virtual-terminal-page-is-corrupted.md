---
title: Adobe Commerce 2.4.0 Braintree Virtual Terminal-Seite beschädigt
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.4.0-Problem, bei dem die Seite "Braintree Virtual Terminal“ nicht die richtigen Benutzeroberflächenelemente lädt, oder eine korrekte Fehlermeldung, wenn Braintree nicht konfiguriert ist.
exl-id: 1d4d762d-2ab3-4752-ad6d-1eb6a179917d
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 Braintree Virtual Terminal-Seite beschädigt

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

Die Benutzeroberfläche der Seite **Braintree Virtual Terminal** ist fehlerhaft, und es wird keine Warnung angezeigt.

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

Anweisungen [ Sie unter „Anwenden eines Composer-Patches von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## Angehängte Dateien
