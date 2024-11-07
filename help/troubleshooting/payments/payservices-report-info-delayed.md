---
title: Berichtsdaten zu verzögerten Zahlungsdiensten
description: In diesem Artikel wird erläutert, warum sich die Berichterstellung für Daten in Zahlungsdiensten verzögern kann.
exl-id: 2f3249d1-be12-45bc-aa73-bef9766509ae
feature: Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Berichtsdaten zu verzögerten Zahlungsdiensten

In diesem Artikel wird erläutert, warum sich die Berichterstellung für Daten in Zahlungsdiensten verzögern kann.

## Betroffene Produkte und Versionen

* [Zahlungsdienste](https://marketplace.magento.com/magento-payment-services.html) ist jetzt mit den Adobe Commerce-Versionen 2.4.0 bis 2.4.4 kompatibel.

## Problem

Die Berichtsdaten von Zahlungsdiensten für die Statusberichte Zahlungsausgabe und Bestellzahlung werden möglicherweise nicht sofort synchronisiert.

Nachdem Sie beispielsweise eine Bestellung in Rechnung gestellt (erfasst) oder ein Kreditmemo für eine Bestellung ausgestellt haben, ist der Status der Bestellung möglicherweise nicht sofort verfügbar.

<u>Zu reproduzierende Schritte</u>:

Voraussetzungen: Eine Bestellung wird mithilfe der Funktion Zahlungsdienste durchgeführt.

1. Eine Bestellung wird in [Admin](https://experienceleague.adobe.com/en/docs/commerce-admin/start/admin/admin) als [fakturiert](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/invoices#create-an-invoice) (oder [storniert](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order) oder [durch Credit Memo](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memos) zurückerstattet).
1. Navigieren Sie zum Bericht Bestellstatus , um Informationen zu dieser Bestellung anzuzeigen.
1. Der Status wird als `AUTHORIZED` angezeigt, was dem Bestellstatus vor der Rechnungsstellung oder anderen Bestellaktionen entspricht.

   Commerce hat keine Daten synchronisiert und an Zahlungsdienste gesendet. Daher wird der neue Bestellstatus vom Bericht noch nicht erkannt.

>[!NOTE]
>
>Dies ist nur ein gängiger Anwendungsfall. Es kann andere Anwendungsfälle geben, in denen eine [Bestellaktion](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/orders#actions) auftritt und die Daten nicht sofort im entsprechenden Bericht verfügbar sind.

<u>Erwartetes Ergebnis</u>:
Berichtsdaten werden sofort ausgefüllt, nachdem eine Aktion für eine Bestellung erfolgt ist.

<u>Tatsächliches Ergebnis</u>:
Es kann zu einer Verzögerung bei sichtbaren Berichtsdaten für gerade abgeschlossene Bestellaktionen kommen. Zahlungsverantwortliche Berichte können eine Verzögerung von 24-48 Stunden verursachen. Berichte zum Bestellstatus können eine Verzögerung von einigen Stunden verursachen.

## Ursache

Es gibt zwei Faktoren, die sich auf diese Verzögerung bei den sichtbaren Daten im Admin auswirken:

* Wie oft Sie Daten aus Commerce über die [Konfiguration in Admin](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/configure-admin.html) synchronisieren (exportieren und beibehalten).
* Zeitrahmen, in dem PayPal Berichtsdaten veröffentlicht.

## Lösung

Für Bestellstatusberichte:

1. Navigieren Sie zu **Verkauf** > **Zahlungsdienste**.
1. Klicken Sie auf **Bestellstatus** , um die Berichtstabelle zum Bestellstatus anzuzeigen.
1. Erzwingen Sie die Neusynchronisierung, indem Sie oben rechts in der Berichtstabelle auf das Symbol **Resync erzwingen** klicken.
1. Sie sollten die letzte aktualisierte Zeitstempeländerung sehen und neue Transaktionen in Ihre Berichtstabelle geladen haben.

Bei PayPal-Payout-Berichten ist das erwartete Ergebnis eine Verzögerung von 24-48 Stunden aufgrund der Abhängigkeit vom Zeitrahmen für die Datenveröffentlichung von PayPal.
