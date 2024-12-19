---
title: 'Adobe Commerce 2.4.2 B2B: Rabatt bleibt bei Änderung der Zahlungsmethode'
description: In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.2 B2B-Problem beschrieben, bei dem ein mit der Zahlungsmethode verknüpfter Rabatt nach einer Änderung der Zahlungsmethode an der Kasse bestehen bleibt. Derzeit ist keine Lösung verfügbar.
exl-id: cd863852-403b-404f-8717-c78c238f5f33
feature: B2B, Orders, Payments, Personalization
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '215'
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

Der Skonto der Zahlungsmethode bleibt auf die Bestellsumme angewendet.  Es wird keine Fehlermeldung angezeigt. Der Besitzer des Geschäfts kann dies sehen, indem er den Auftragsverlauf überprüft.

<u>Erwartete Ergebnisse</u> : Der Rabatt für die Zahlungsmethode wird erwartungsgemäß aus der Bestellsumme entfernt.

## Lösung

Derzeit ist keine Lösung verfügbar.
