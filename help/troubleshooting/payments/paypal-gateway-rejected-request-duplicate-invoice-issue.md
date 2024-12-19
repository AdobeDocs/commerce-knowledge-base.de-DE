---
title: Anfrage für PayPal-Gateway abgelehnt - Problem mit doppelter Rechnung
description: Dieser Artikel bietet eine Fehlerbehebung für das Problem mit der zurückgewiesenen PayPal-Gateway-Rechnung - doppelte Rechnung.
exl-id: b6c4ede1-97a5-4db3-9b05-ab979cf809b3
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Anfrage für PayPal-Gateway abgelehnt - Problem mit doppelter Rechnung

Dieser Artikel bietet eine Fehlerbehebung für das Problem mit der zurückgewiesenen PayPal-Gateway-Rechnung - doppelte Rechnung.

Beim Einreichen der Zahlung wird dem Kunden möglicherweise ein Fehler bei einer doppelten Rechnung angezeigt:

>PayPal-Gateway hat Anfrage abgelehnt. Für diese InvoiceID wurde bereits eine Zahlung geleistet (\#10412: Doppelte Rechnung)

Das Problem tritt auf, wenn Rechnungen mit denselben IDs mehrmals an PayPal gesendet werden.

Um das Problem zu beheben, lassen Sie in den Zahlungseingangsvoreinstellungen von PayPal mehrere Zahlungen pro Rechnungs-ID zu. Bei einer Änderung akzeptiert PayPal Zahlungen ohne Fehlermeldungen, auch für Rechnungen mit doppelten IDs.

## Betroffene Versionen

* Adobe Commerce On-Premise, alle Versionen
* Adobe Commerce auf Cloud-Infrastruktur, alle Versionen

## Problem

Beim Senden der Zahlung wird die folgende Fehlermeldung angezeigt:

```
... main.CRITICAL: Exception message: PayPal gateway has rejected request. Payment has already been made for this InvoiceID (#10412: Duplicate invoice).
```

PayPal kann die Zahlung nicht verarbeiten und die Bestellung abschließen.

## Ursache

Die Fehlermeldung wird angezeigt, wenn Rechnungen mit derselben ID mehrmals an PayPal gesendet werden.

Dies kann vorkommen, wenn dieselben Anmeldeinformationen für mehrere Adobe Commerce-Sites verwendet werden (sogar für die lokale und die Staging-Umgebung). Besondere Szenarien könnten die folgenden sein:

* Mehrere Geschäfte übermitteln Rechnungen an PayPal und verwenden dieselben Rechnungskennungen
* Ein neuer Store sendet eine Rechnung mit einer ID, die zuvor von einem alten Store gesendet wurde

Standardmäßig lässt PayPal die Verarbeitung derselben Rechnung nicht zweimal zu.

## Lösung

Ändern Sie Ihr PayPal-Profil, um mehrere Zahlungen pro Rechnungs-ID zuzulassen. Sie müssen diese Änderungen über PayPal vornehmen.

1. Melden Sie sich bei Ihrem Konto unter [https://www.paypal.com](https://www.paypal.com/) an.
1. Klicken Sie **Profil** > **Profil und Einstellungen** (obere rechte Ecke).
1. Gehen Sie zu **Meine Verkaufstools**.
1. Navigieren Sie zu **Bezahlt werden und mein Risiko verwalten** > **Zahlungen blockieren** und klicken Sie auf **Aktualisieren**.
1. **Verkaufsvoreinstellungen** klicken Sie auf **Zahlungseingangsvoreinstellungen**.
1. Wählen Sie **&quot;** blockieren“ die Option **Nein, mehrere Zahlungen pro Rechnungs-ID zulassen**.    ![PAYPAL_ALLOW_MULTIPLE_PAYMENTS_PER_INVOICE_ID.png](assets/paypal_allow_multiple_payments_per_invoice_id.png)
1. Scrollen Sie nach unten und klicken Sie auf **Speichern**.

## Weitere Informationen

* [Sperren Sie versehentliche ](https://developer.paypal.com/docs/admin/setup-account/#block-accidental-payments) auf PayPal-Entwicklerdokumenten.
* PayPal-Zahlungen in unserem Benutzerhandbuch:
   * [PayPal Express-Checkout](/docs/commerce-admin/stores-sales/payments/paypal/paypal-express-checkout.html)
   * [Andere PayPal-Lösungen](/docs/commerce-admin/stores-sales/payments/paypal/paypal.html)
* In unserer Entwicklerdokumentation:
   * [Einrichten von PayPal-Zahlungsmethoden für Adobe Commerce in der Cloud-Infrastruktur](/docs/commerce-cloud-service/user-guide/configure-store/paypal.html)
   * [Zahlungsintegrationen](https://developer.adobe.com/commerce/php/development/payments-integrations/)
