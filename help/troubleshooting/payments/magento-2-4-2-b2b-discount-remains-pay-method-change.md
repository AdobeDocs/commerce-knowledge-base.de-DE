---
title: "Adobe Commerce 2.4.2 B2B: Rabatt bleibt Zahlungsmethodenänderung erhalten"
description: In diesem Artikel wird ein bekanntes B2B-Problem in Adobe Commerce 2.4.2 beschrieben, bei dem ein durch die Zahlungsmethode gebundener Rabatt nach einer Änderung der Zahlungsmethode beim Checkout beibehalten wird. Derzeit steht keine Lösung zur Verfügung.
exl-id: cd863852-403b-404f-8717-c78c238f5f33
feature: B2B, Orders, Payments, Personalization
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Adobe Commerce 2.4.2 B2B: Rabatt bleibt Zahlungsmethodenänderung erhalten

In diesem Artikel wird ein bekanntes B2B-Problem in Adobe Commerce 2.4.2 beschrieben, bei dem ein durch die Zahlungsmethode gebundener Rabatt nach einer Änderung der Zahlungsmethode beim Checkout beibehalten wird. Derzeit steht keine Lösung zur Verfügung.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.2
* Adobe Commerce in Cloud-Infrastruktur 2.4.2
* B2B für Adobe Commerce 1.3.1


## Problem

<u>Zu reproduzierende Schritte</u> :

1. Warenkorb erstellen **Preisregel** die mit einer Zahlungsmethode verknüpft ist (Beispiel: Paypal-Benutzer erhalten einen Rabatt von 20 %.)
1. Erstellen Sie eine Bestellung (Bestellformular) und wählen Sie Paypal als Zahlungsmethode aus. Der Rabatt wird angewendet.
1. Die Bestellung wird genehmigt.
1. Gehen Sie zur Zahlungsseite, um die Bestellung abzuschließen.
1. Wählen Sie eine andere Zahlungsmethode aus.

<u>Tatsächliche Ergebnisse</u> :

Der Rabatt für die Zahlungsmethode bleibt auf die Bestellsumme angewendet.  Es wird keine Fehlermeldung angezeigt. Der Store-Eigentümer kann dies durch Überprüfen des Bestellverlaufs sehen.

<u>Erwartete Ergebnisse</u> :Der Rabatt für die Zahlungsmethode wird wie erwartet aus der Bestellsumme entfernt.

## Lösung

Derzeit steht keine Lösung zur Verfügung.
