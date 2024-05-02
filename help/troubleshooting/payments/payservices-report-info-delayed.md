---
title: Berichtsdaten zu verzögerten Zahlungsdiensten
description: In diesem Artikel wird erläutert, warum sich die Berichterstellung für Daten in Zahlungsdiensten verzögern kann.
exl-id: 2f3249d1-be12-45bc-aa73-bef9766509ae
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
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

1. Eine Bestellung ist [fakturiert](https://docs.magento.com/user-guide/sales/invoice-create.html) (oder [abgebrochen](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order) oder [über Kreditkarte zurückerstattet](https://docs.magento.com/user-guide/sales/credit-memos.html)) in der [Admin](https://docs.magento.com/user-guide/stores/admin.html).
1. Navigieren Sie zum Bericht Bestellstatus , um Informationen zu dieser Bestellung anzuzeigen.
1. Der Status wird angezeigt als `AUTHORIZED`: der Auftragsstatus vor der Rechnungsstellung oder einer anderen Bestellaktion.

   Commerce hat keine Daten synchronisiert und an Zahlungsdienste gesendet. Daher wird der neue Bestellstatus vom Bericht noch nicht erkannt.

>[!NOTE]
>
>Dies ist nur ein gängiger Anwendungsfall. In anderen Anwendungsfällen kann es vorkommen, dass ein [Bestellaktion](https://docs.magento.com/user-guide/sales/order-actions.html) auftritt und die Daten nicht sofort im entsprechenden Bericht verfügbar sind.

<u>Erwartetes Ergebnis</u>: Berichtsdaten werden sofort ausgefüllt, nachdem eine Aktion für eine Bestellung ausgeführt wurde.

<u>Tatsächliches Ergebnis</u>: Bei gerade abgeschlossenen Bestellaktionen kann es zu einer Verzögerung bei den angezeigten Berichtsdaten kommen. Zahlungsverantwortliche Berichte können eine Verzögerung von 24-48 Stunden verursachen. Berichte zum Bestellstatus können eine Verzögerung von einigen Stunden verursachen.

## Ursache

Es gibt zwei Faktoren, die sich auf diese Verzögerung bei den sichtbaren Daten im Admin auswirken:

* Wie oft Sie Daten aus Commerce synchronisieren (exportieren und beibehalten), über [Konfiguration in der Admin-Konfiguration](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/configure-admin.html).
* Zeitrahmen, in dem PayPal Berichtsdaten veröffentlicht.

## Lösung

Für Bestellstatusberichte:

1. Navigieren Sie zu **Vertrieb** > **Zahlungsdienste**.
1. Klicks **Bestellstatus** , um die Tabelle mit den Berichten zum Bestellstatus anzuzeigen.
1. Erzwingen der Neusynchronisierung durch Klicken auf **erzwingen resync** rechts oben in der Berichtstabelle angezeigt.
1. Sie sollten die letzte aktualisierte Zeitstempeländerung sehen und neue Transaktionen in Ihre Berichtstabelle geladen haben.

Bei PayPal-Payout-Berichten ist das erwartete Ergebnis eine Verzögerung von 24-48 Stunden aufgrund der Abhängigkeit vom Zeitrahmen für die Datenveröffentlichung von PayPal.
