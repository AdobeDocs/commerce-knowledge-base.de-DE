---
title: Fehlerbehebung bei PayPal in Adobe Commerce
description: Dieser Artikel bietet Lösungen für Probleme bei der Verarbeitung von Zahlungen über PayPal, insbesondere die PayFlow Pro-Lösung. Einige Empfehlungen in diesem Artikel scheinen offensichtlich zu sein. Wir bitten Sie, die in dieser Wissensdatenbank aufgelisteten Fehlerbehebungsoptionen auszuführen und alle Informationen in die eingegebenen Tickets aufzunehmen. Support-Mitarbeiter von Adobe Commerce oder PayPal werden Sie bitten, diese Schritte bei der Fehlerdiagnose durchzuführen.
exl-id: f0772515-8456-4f08-84b4-aeef44516f2a
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# Fehlerbehebung bei PayPal in Adobe Commerce

Dieser Artikel bietet Lösungen für Probleme bei der Verarbeitung von Zahlungen über PayPal, insbesondere die PayFlow Pro-Lösung. Einige Empfehlungen in diesem Artikel scheinen offensichtlich zu sein. Wir bitten Sie, die in dieser Wissensdatenbank aufgelisteten Fehlerbehebungsoptionen auszuführen und alle Informationen in die eingegebenen Tickets aufzunehmen. Support-Mitarbeiter von Adobe Commerce oder PayPal werden Sie bitten, diese Schritte bei der Fehlerdiagnose durchzuführen.

## Häufige Probleme

Die meisten Probleme mit PayPal-Zahlungen weisen ähnliche Symptome auf: Nachdem Sie die Zahlungskartendetails angegeben und zum Checkout übergegangen sind, wird die Zahlung nicht verarbeitet. Stattdessen kann es zu einer Fehlermeldung, einer fehlgeschlagenen Verarbeitung der Zahlung oder sogar zu einer leeren Seite kommen.

## Überprüfen der Anmeldeinformationen, Schlüssel verschlüsseln und Lizenzen

Mögliche Probleme: Fehlabdrücke in Kontodetails (Benutzernamen, Passwörter), ungültige Konten, abgelaufene oder nicht angegebene Lizenzen, ungültige öffentliche und persönliche Schlüssel und viele andere Aspekte. Um diese Probleme zu finden, müssen Sie möglicherweise auch Ihre Zahlungskonfigurationseinstellungen überprüfen.

## Anwenden konsistenter Einstellungen in Adobe Commerce und PayPal

Vergewissern Sie sich, dass Sie dieselben Einstellungen angewendet und dieselben Funktionen in den Kontoeinstellungen für Commerce Admin und PayPal aktiviert haben.

### Problem mit Beispieleinstellungen

Bei der Anwendung der PayPal Express Checkout-Lösung müssen Transaktionen, die auf AVS-/CSC-Antworten basieren, unter **PayPal Manager** (Diensteinstellungen > Einrichten > Sicherheitsoptionen) und in **Commerce Admin** ( **Stores** > Konfiguration > **Vertrieb** > **Zahlungsmethoden** ...).
![magento_paypal_settings_2.4.1.png](assets/magento_paypal_settings_2.4.1.png)
Weitere Informationen finden Sie in der Dokumentation: [PayPal](https://www.paypalobjects.com/en_US/vhelp/paypalmanager_help/setup.htm) und [Adobe Commerce](/docs/commerce-admin/stores-sales/payments/paypal/paypal-express-checkout.html) in unserem Benutzerhandbuch.

## Referenztransaktionen zulassen

Wenn Ihre PayPal-Zahlungsmethode API mit Abrechnungsvereinbarungen und Referenztransaktionen beinhaltet, stellen Sie sicher, dass sie in Ihren Einstellungen aktiviert und korrekt konfiguriert sind.

### Zusätzliche Fehlerbehebung

Siehe die folgenden Artikel:

* [PayPal Gateway Anfrage abgelehnt - Problem mit doppelten Rechnungen](/help/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.md) in unserer Wissensdatenbank.
* [Inkrementierungs-ID für neue Store-Entität ändern](/help/how-to/general/change-increment-id-for-a-db-entity-order-invoice-credit-memo-etc-on-particular-store.md) in unserer Wissensdatenbank.

## Support kontaktieren, um erweiterte Zahlungslogs zu erfassen

Um komplizierte Zahlungsprobleme zu beheben, kann das Adobe Commerce-Supportteam Sie bitten, einen speziellen Patch anzuwenden, um eine erweiterte Zahlungsprotokollierung zu ermöglichen. In diesem Fall sollten die folgenden Schritte ausgeführt werden:

[Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) mit den folgenden Details:

* Geben Sie Ihr Problem mit so vielen Details wie möglich an.
* Führen Sie die Schritte auf, die Sie mit diesem Artikel, der Wissensdatenbank und anderen Ressourcen versucht haben. Schließen Sie alle Ergebnisse ein.
* Fordern Sie einen Patch für die erweiterte Zahlungsprotokollierung (Referenznummer MDVA-4352) und Anweisungen zum Anwenden des Patches an.

Wenn Sie den Patch &quot;Erweiterte Zahlungsprotokollierung&quot;erhalten:

* Wenden Sie den Patch an.
* Erfassen Sie Protokolle und fügen Sie sie an Ihre [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
* Warten Sie auf weitere Empfehlungen des Adobe Commerce-Supportteams.
