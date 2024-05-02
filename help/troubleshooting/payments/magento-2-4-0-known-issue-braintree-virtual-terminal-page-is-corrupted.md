---
title: Adobe Commerce 2.4.0 Braintree Virtual Terminal-Seite beschädigt
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.4.0-Problem, bei dem die Braintree Virtual Terminal-Seite die entsprechenden Benutzeroberflächenelemente nicht lädt, oder eine entsprechende Fehlermeldung, wenn Braintree nicht konfiguriert ist.
exl-id: 1d4d762d-2ab3-4752-ad6d-1eb6a179917d
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 Braintree Virtual Terminal-Seite beschädigt

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.4.0-Problem, bei dem die Braintree Virtual Terminal-Seite die entsprechenden Benutzeroberflächenelemente nicht lädt, oder eine entsprechende Fehlermeldung, wenn Braintree nicht konfiguriert ist.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.4.0
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

## Problem

### Szenario 1: Braintree-Zahlungsmethode ist konfiguriert

<u>Zu reproduzierende Schritte:</u>

Navigieren Sie in Commerce Admin zu **Vertrieb** > **Braintree Virtual Terminal** . ** **

<u>Erwartetes Ergebnis:</u>

Die **Braintree Virtual Terminal** Seite wird mit der richtigen Benutzeroberfläche geladen.

<u>Ergebnis:</u>

Die Benutzeroberfläche der **Braintree Virtual Terminal** Seite ist kaputt.

### Szenario 2: Braintree-Zahlungsmethode ist konfiguriert

<u>Zu reproduzierende Schritte:</u>

Navigieren Sie in Commerce Admin zu **Vertrieb** > **Braintree Virtual Terminal** . ** **

<u>Erwartetes Ergebnis:</u>

Die **Braintree Virtual Terminal** -Seite mit der richtigen Benutzeroberfläche geladen wird und ein Warnhinweis angezeigt wird, der darüber informiert, dass Braintree noch nicht konfiguriert ist.

<u>Ergebnis:</u>

Die Benutzeroberfläche der **Braintree Virtual Terminal** -Seite beschädigt ist und keine Warnung angezeigt wird.

## Lösung

Wenden Sie den in diesem Artikel bereitgestellten Patch an.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[BUNDLE-2670-composer.patch](assets/BUNDLE-2670-composer.patch.zip)

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce auf Cloud-Infrastruktur 2.4.0
* Adobe Commerce vor Ort 2.4.0

## Anwenden des Pflasters

Siehe [Anwenden eines von Adobe bereitgestellten Composer-Patches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) für Anweisungen.

## Attached Files
