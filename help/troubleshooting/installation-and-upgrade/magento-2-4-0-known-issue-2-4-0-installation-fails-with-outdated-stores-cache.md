---
title: Die Installation von Adobe Commerce 2.4.0 schlägt mit veraltetem Speicher-Cache fehl
description: 'Dieser Artikel bietet eine Lösung für den Fall, dass Ihre Adobe Commerce 2.4.0-Installation mit der folgenden Fehlermeldung fehlschlägt: *Die Standard-Website ist nicht definiert. Legen Sie die Website fest und versuchen Sie es erneut.* Wird in der Konsole angezeigt.'
exl-id: 0680199b-7e47-4a8c-91fe-9f6c32839a0e
feature: B2B, Cache, Console, Install, Upgrade
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Die Installation von Adobe Commerce 2.4.0 schlägt mit veraltetem Speicher-Cache fehl

Dieser Artikel bietet eine Lösung für den Fall, dass Ihre Adobe Commerce 2.4.0-Installation mit der folgenden Fehlermeldung fehlschlägt: *Die Standard-Website ist nicht definiert. Legen Sie die Website fest und versuchen Sie es erneut.* in der Konsole angezeigt.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.4.0
* Adobe Commerce On-Premises 2.4.0

## Problem

<u>Voraussetzungen:</u>
Eine Erweiterung eines Drittanbieters mit Abhängigkeiten von APIs für das Store -Modul in CLI-Befehlen wird wie in `composer.json` erforderlich konfiguriert. Dies führt dazu, dass die Installation von Adobe Commerce 2.4.0 mit einer Fehlermeldung fehlschlägt: *Die Standard-Website ist nicht definiert. Legen Sie die Website fest und versuchen Sie es erneut.* in der Konsole angezeigt.

## Ursache

Das Problem tritt bei Erweiterungen von Drittanbietern auf, deren CLI-Befehle von Stores abhängig sind. Einer sind die Amazon-Vertriebskanäle.

## Lösung

Vor der Installation von Adobe Commerce 2.4.0 müssen Händler:

1. Entfernen Sie diese Erweiterungen von Drittanbietern aus `composer.json`.
1. Installieren Sie Adobe Commerce ohne Erweiterungen.
1. Fügen Sie die Erweiterungen nach der Installation hinzu.

Das Problem wird im Umfang der Version 2.4.1 behoben.

## Weiterführende Informationen finden Sie in unserer Support-Wissensdatenbank:

* [Bekanntes Problem in Adobe Commerce 2.4.0: fehlende Kennzeichnung „Rückerstattung“ in Klarna](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Auf der Seite „Neue Bestellung erstellen“ in „Admin“ fehlen zwei Schaltflächen](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Adobe Commerce 2.4.0, 2.4.1: Teilrechnungsprobleme mit Braintree Venmo aktivieren](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Fehlermeldung bei Auswahl der lokalen Zahlungsmethode, die für einige Länder während des Checkouts angezeigt wird](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Amazon Pay aktiviert, Zahlungsmethoden fehlen, wenn die Rückgabe zur standardmäßigen Kasse verwendet wird](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Adobe Commerce 2.4.0 B2B-Admin kann kein konfigurierbares Produkt zum Angebot hinzufügen](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0 - Aktualisierung der Aktivitäten des Kunden funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 bekanntes Problem - Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Die Schaltfläche „Auswahl zu meinem Warenkorb hinzufügen“ funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)

