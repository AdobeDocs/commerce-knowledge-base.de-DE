---
title: Die Installation von Adobe Commerce 2.4.0 schlägt mit veraltetem Speicher-Cache fehl
description: 'Dieser Artikel bietet eine Lösung für den Fall, dass Ihre Adobe Commerce 2.4.0-Installation mit der folgenden Fehlermeldung fehlschlägt: *Die Standard-Website ist nicht definiert. Legen Sie die Website fest und versuchen Sie es erneut.* wird in der Konsole angezeigt.'
exl-id: 0680199b-7e47-4a8c-91fe-9f6c32839a0e
feature: B2B, Cache, Console, Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '291'
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
* [Adobe Commerce 2.4.0, 2.4.1: Teilrechnungsprobleme mit Braintree Venmo aktivieren](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Fehlermeldung bei Auswahl der lokalen Zahlungsmethode, die für einige Länder während des Checkouts angezeigt wird](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Amazon Pay aktiviert, Zahlungsmethoden fehlen, wenn die Rückgabe zur standardmäßigen Kasse verwendet wird](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)

