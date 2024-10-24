---
title: Bekanntes Problem in Adobe Commerce 2.4.0 - Exportsteuersätze funktionieren nicht
description: Dieser Artikel bietet eine Lösung für ein bekanntes Problem mit Adobe Commerce 2.4.0, bei dem die Schaltfläche "Exportsteuersätze"nicht funktioniert.
exl-id: 29a34a1f-d23a-43cb-ac1f-8711ce25fa6c
feature: Data Import/Export, Orders
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Bekanntes Problem in Adobe Commerce 2.4.0 - Exportsteuersätze funktionieren nicht

Dieser Artikel bietet eine Lösung für ein bekanntes Problem mit Adobe Commerce 2.4.0, bei dem die Schaltfläche **Exportsteuersätze** nicht funktioniert.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.4.0
* Adobe Commerce vor Ort 2.4.0

## Problem

<u>Zu reproduzierende Schritte:</u>

1. Wechseln Sie zum Commerce-Admin-Bedienfeld > **Geschäfte** > **Steuerregeln**.
1. Klicken Sie auf die Schaltfläche **Neue Steuerregel hinzufügen** .
1. Klicken Sie auf den Text der Schaltfläche **Steuersätze exportieren** .

   ![magento_export_tax_rates.png](assets/mceclip0.png)

<u>Erwartetes Ergebnis</u>:

Ein `tax_rates.csv` -Dateidownload mit Steuersätzen.

<u>Tatsächliches Ergebnis</u>:

Es wird keine CSV-Datei heruntergeladen.

## Lösung

Problemumgehung:

Klicken Sie auf den unteren linken Rand der Schaltfläche **Steuersätze exportieren** , um die Datei `tax_rates.csv` zu exportieren.

![magento_export_tax_rates.png](assets/mceclip1.png)

Es ist geplant, das Problem in einem Patch 2.4.1 zu beheben.

## Verwandtes Lesen

In unserer Support-Wissensdatenbank:

* [Bekanntes Problem mit Adobe Commerce 2.4.0: Braintree-Zahlungsmethoden werden beim Checkout mit mehreren Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md).
* [Bekanntes Problem mit Adobe Commerce 2.4.0 - Aktualisierung der Kundenaktivitäten funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md).
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Rohdaten von Nachrichten werden in der Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md).
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Die Schaltfläche &quot;Auswahl zum Warenkorb hinzufügen&quot;funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md).
