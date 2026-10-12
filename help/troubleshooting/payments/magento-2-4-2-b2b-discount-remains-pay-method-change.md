---
title: 'Adobe Commerce 2.4.2 B2B: Rabatt bleibt bei Änderung der Zahlungsmethode'
description: In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.2 B2B-Problem beschrieben, bei dem ein mit der Zahlungsmethode verknüpfter Rabatt nach einer Änderung der Zahlungsmethode an der Kasse bestehen bleibt. Derzeit ist keine Lösung verfügbar.
exl-id: cd863852-403b-404f-8717-c78c238f5f33
feature: B2B, Orders, Payments, Personalization
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
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
source-wordcount: '210'
ht-degree: 0%
---
# Adobe Commerce 2.4.2 B2B: Rabatt bleibt bei Änderung der Zahlungsmethode

In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.2 B2B-Problem beschrieben, bei dem ein mit der Zahlungsmethode verknüpfter Rabatt nach einer Änderung der Zahlungsmethode an der Kasse bestehen bleibt. Derzeit ist keine Lösung verfügbar.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.2
* Adobe Commerce auf Cloud-Infrastruktur 2.4.2
* B2B für Adobe Commerce 1.3.1


## Problem

<u>Schritte zur Reproduktion</u> :

1. Erstellen Sie einen Warenkorb **Preisregel** der an eine Zahlungsmethode gebunden ist (Beispiel: PayPal-Benutzer erhalten einen Rabatt von 20 %).
1. Erstellen Sie eine Bestellung (PO) und wählen Sie PayPal als Zahlungsmethode. Der Rabatt wird angewendet.
1. Die Bestellung ist genehmigt.
1. Gehen Sie zur Zahlungsseite, um die Bestellung abzuschließen.
1. Wählen Sie eine andere Zahlungsmethode aus.

<u>Tatsächliche Ergebnisse</u> :

Der Skonto der Zahlungsmethode bleibt auf die Bestellsumme angewendet.  Keine Fehlermeldung angezeigt.Der Geschäftsinhaber kann diesen Fehler im Bestellverlauf sehen.

<u>Erwartete Ergebnisse</u> :The Rabatt auf die Zahlungsmethode wird wie erwartet aus der Bestellsumme entfernt.

## Lösung

Derzeit ist keine Lösung verfügbar.
