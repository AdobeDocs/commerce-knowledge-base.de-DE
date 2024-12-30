---
title: Zahlungsmethoden werden an der Kasse mit mehreren Adressen nicht angezeigt
description: In diesem Artikel wird erläutert, dass die meisten Zahlungsmethoden an der Kasse nicht angezeigt werden, wenn mehrere Versandadressen angegeben sind, da die Funktionalität nur für Cybersource implementiert ist.
exl-id: 68a9ee77-d0ef-43c5-9667-6d099b797666
feature: Checkout, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Zahlungsmethoden werden an der Kasse mit mehreren Adressen nicht angezeigt

In diesem Artikel wird erläutert, dass die meisten Zahlungsmethoden an der Kasse nicht angezeigt werden, wenn mehrere Versandadressen angegeben sind, da die Funktionalität nur für Cybersource implementiert ist.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.x.x
* Adobe Commerce auf Cloud-Infrastruktur 2.x.x

>[!NOTE]
>
>Die zentrale Adobe Commerce Cybersource-Zahlungsintegration ist seit 2.3.3 veraltet und wird in 2.4.0 vollständig entfernt. Verwenden Sie stattdessen die [offizielle Erweiterung](https://marketplace.magento.com/cybersource-global-payment-management.html) vom Marketplace.

## Problem

<u>Voraussetzungen</u>: Aktivieren und konfigurieren Sie in Commerce Admin die Zahlungsmethoden PayPal und Cybersource und aktivieren Sie Multishipping für Ihren Shop.

<u>Schritte zur Reproduktion</u>:

1. Fügen Sie in der Storefront mehrere Produkte zum Warenkorb hinzu.
1. Navigieren Sie zur Seite mit dem Warenkorb.
1. Klicken Sie **Mit mehreren Adressen auschecken**.
1. Anmelden oder Konto erstellen.
1. Produkte zwischen den Adressen auf der Seite Versand an mehrere Adressen aufteilen.
1. Klicken Sie **Zu Versandinformationen gehen**.
1. Wählen Sie die Versandarten für jede Lieferung aus.
1. Klicken Sie **Weiter zu Rechnungsinformationen**.

<u>Erwartetes Ergebnis</u>: PayPal und Cybersource stehen als Zahlungsoptionen zur Verfügung.

<u>Tatsächliches Ergebnis</u>: Nur Cybersource wird als verfügbare Zahlungsoption angezeigt.

## Ursache

Derzeit ist Cybersource die einzige unterstützte Live-Zahlungsmethode für den Multishipping-Checkout, beginnend mit Version 2.2.4. Die Unterstützung für Multishipping wird wahrscheinlich für jede Zahlungsmethode einzeln erstellt. Genaue Daten oder Versionsnummern können derzeit nicht angegeben werden.
