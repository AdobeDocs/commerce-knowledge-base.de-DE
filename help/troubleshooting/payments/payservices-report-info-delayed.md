---
title: Berichtsdaten zu verzögerten Zahlungsdiensten
description: In diesem Artikel wird erläutert, warum sich die Berichterstellung zu Daten in Payment Services verzögern kann.
exl-id: 2f3249d1-be12-45bc-aa73-bef9766509ae
feature: Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Berichtsdaten zu verzögerten Zahlungsdiensten

In diesem Artikel wird erläutert, warum sich die Berichterstellung zu Daten in Payment Services verzögern kann.

## Betroffene Produkte und Versionen

* [Payment Services](https://marketplace.magento.com/magento-payment-services.html) ist jetzt mit den Adobe Commerce-Versionen 2.4.0 bis 2.4.4 kompatibel.

## Problem

Die Berichtsdaten von Payment Services für die Berichte „Auszahlung“ und „Zahlungsstatus bei Bestellung“ werden möglicherweise nicht sofort synchronisiert.

Nachdem Sie beispielsweise eine Bestellung fakturiert (erfasst) oder eine Gutschrift für eine Bestellung ausgestellt haben, ist der Status der Bestellung möglicherweise nicht sofort verfügbar.

<u>Schritte zur Reproduktion</u>:

Voraussetzungen: Eine Bestellung wird über die Zahlungsdienstfunktion aufgegeben.

1. Eine Bestellung wird [fakturiert](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/order-management/invoices#create-an-invoice) (oder [storniert](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order) oder [per Gutschrift ](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memos)) in [Admin](https://experienceleague.adobe.com/de/docs/commerce-admin/start/admin/admin).
1. Navigieren Sie zur Auswertung „Zahlungsstatus der Bestellung“, um Informationen zu dieser Bestellung anzuzeigen.
1. Der Status wird als `AUTHORIZED` angezeigt, d. h. der Bestellstatus vor der Fakturierung oder einer anderen Bestellaktion.

   Commerce hat die Daten nicht synchronisiert und an Payment Services gesendet, sodass der neue Bestellstatus vom Bericht noch nicht erkannt wird.

>[!NOTE]
>
>Dies ist nur ein gängiger Anwendungsfall. Es kann andere Anwendungsfälle geben, in denen [Bestellaktion](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/order-management/orders/orders#actions) auftritt und die Daten im entsprechenden Bericht nicht sofort verfügbar sind.

<u>Erwartetes Ergebnis</u>:
Berichtsdaten werden sofort nach einer Aktion für eine Bestellung ausgefüllt.

<u>Tatsächliches </u>:
Bei gerade abgeschlossenen Bestellaktionen kann es zu einer Verzögerung bei den sichtbaren Berichtsdaten kommen. Auszahlungsberichte können eine Verzögerung von 24-48 Stunden verursachen. Berichte zum Status der Bestellzahlung können mit einer Verzögerung von einigen Stunden verbunden sein.

## Ursache

Es gibt zwei Faktoren, die diese Verzögerung bei der Anzeige sichtbarer Daten in der Admin-Instanz beeinflussen:

* Wie oft Sie Daten aus Commerce über (Konfiguration im Admin[ synchronisieren (exportieren und beibehalten](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/configure-admin.html?lang=de).
* Zeitrahmen, in dem PayPal Berichtsdaten veröffentlicht.

## Lösung

Für Berichte zum Status der Bestellzahlung:

1. Navigieren Sie **Verkauf** > **Zahlungsdienste**.
1. Klicken Sie **Zahlungsstatus bestellen**, um die Tabelle mit den Zahlungsstatus-Berichten anzuzeigen.
1. Erzwingt die Neusynchronisierung durch Klicken auf **Erzwingt die Neusynchronisierung** in der oberen rechten Ecke der Berichttabelle.
1. Sie sollten die letzte aktualisierte Zeitstempeländerung und neue Transaktionen sehen, die in Ihre Berichtstabelle geladen wurden.

Bei PayPal-Auszahlungsberichten ist das erwartete Ergebnis eine Verzögerung von 24-48 Stunden aufgrund der Abhängigkeit vom Zeitrahmen der Datenveröffentlichung von PayPal.
