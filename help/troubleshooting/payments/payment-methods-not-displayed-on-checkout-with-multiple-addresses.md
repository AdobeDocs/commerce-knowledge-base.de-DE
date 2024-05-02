---
title: Zahlungsmethoden werden beim Checkout nicht mit mehreren Adressen angezeigt
description: In diesem Artikel wird erläutert, dass die meisten Zahlungsmethoden beim Checkout nicht angezeigt werden, wenn mehrere Versandadressen angegeben sind, da die Funktionalität nur für Cybersource implementiert ist.
exl-id: 68a9ee77-d0ef-43c5-9667-6d099b797666
feature: Checkout, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Zahlungsmethoden werden beim Checkout nicht mit mehreren Adressen angezeigt

In diesem Artikel wird erläutert, dass die meisten Zahlungsmethoden beim Checkout nicht angezeigt werden, wenn mehrere Versandadressen angegeben sind, da die Funktionalität nur für Cybersource implementiert ist.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premise 2.x.x
* Adobe Commerce auf Cloud-Infrastruktur 2.x.x

>[!NOTE]
>
>Die zentrale Adobe Commerce Cybersource-Zahlungsintegration ist seit 2.3.3 veraltet und wird in 2.4.0 vollständig entfernt. Verwenden Sie die [offizielle Erweiterung](https://marketplace.magento.com/cybersource-global-payment-management.html) vom Marketplace aus.

## Problem

<u>Voraussetzungen</u>: Aktivieren und konfigurieren Sie in Commerce Admin die Zahlungsmethoden PayPal und Cybersource und aktivieren Sie Multishipping für Ihren Store.

<u>Zu reproduzierende Schritte</u>:

1. Fügen Sie im Schaufenster mehrere Produkte zum Warenkorb hinzu.
1. Gehen Sie zur Warenkorbseite.
1. Klicks **Mit mehreren Adressen auschecken**.
1. Melden Sie sich an oder erstellen Sie ein Konto.
1. Teilen Sie Produkte zwischen den Adressen auf der Seite &quot;Versand an mehrere Adressen&quot; auf.
1. Klicks **Navigieren Sie zu Versandinformationen .**.
1. Wählen Sie Versandmethoden für jede Sendung aus.
1. Klicks **Weiter zu Rechnungsinformationen**.

<u>Erwartetes Ergebnis</u>: PayPal und Cybersource sind als Zahlungsoptionen verfügbar.

<u>Tatsächliches Ergebnis</u>: Nur Cybersource wird als verfügbare Zahlungsoption angezeigt.

## Ursache

Derzeit ist Cybersource die einzige unterstützte Live-Zahlungsmethode für Multishipping Checkout, ab Version 2.2.4. Die Unterstützung für Multishipping wird wahrscheinlich für jede Zahlungsmethode einzeln erstellt. Derzeit können keine genauen Daten oder Versionsnummern angegeben werden.
