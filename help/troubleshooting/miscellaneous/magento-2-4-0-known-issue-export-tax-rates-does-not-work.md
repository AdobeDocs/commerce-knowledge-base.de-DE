---
title: Bekanntes Problem in Adobe Commerce 2.4.0 - Exportsteuersätze funktionieren nicht
description: Dieser Artikel bietet eine Lösung für ein bekanntes Problem mit Adobe Commerce 2.4.0, bei dem die Schaltfläche "Exportsteuersätze"nicht funktioniert.
exl-id: 29a34a1f-d23a-43cb-ac1f-8711ce25fa6c
feature: Data Import/Export, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Bekanntes Problem in Adobe Commerce 2.4.0 - Exportsteuersätze funktionieren nicht

Dieser Artikel bietet eine Lösung für ein bekanntes Problem mit Adobe Commerce 2.4.0, bei dem die Variable **Ausfuhrsteuersätze** -Schaltfläche funktioniert nicht.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.4.0
* Adobe Commerce vor Ort 2.4.0

## Problem

<u>Zu reproduzierende Schritte:</u>

1. Navigieren Sie zum Commerce Admin Panel > **Stores** > **Steuervorschriften**.
1. Klicken Sie auf **Neue Steuerregel hinzufügen** Schaltfläche.
1. Klicken Sie auf den Text der **Ausfuhrsteuersätze** Schaltfläche.

   ![magento_export_tax_rates.png](assets/mceclip0.png)

<u>Erwartetes Ergebnis</u>:

A `tax_rates.csv` Dateidownloads mit Steuersätzen.

<u>Tatsächliches Ergebnis</u>:

Es wird keine CSV-Datei heruntergeladen.

## Lösung

Problemumgehung:

Klicken Sie auf den unteren linken Rand des **Ausfuhrsteuersätze** -Schaltfläche zum Exportieren `tax_rates.csv` -Datei.

![magento_export_tax_rates.png](assets/mceclip1.png)

Es ist geplant, das Problem in einem Patch 2.4.1 zu beheben.

## Verwandtes Lesen

In unserer Support-Wissensdatenbank:

* [Bekanntes Problem in Adobe Commerce 2.4.0: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md).
* [Bekanntes Problem bei der Erstellung von Versandbeschriftungen in Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md).
* [Bekanntes Problem mit Adobe Commerce 2.4.0 - Aktualisierung der Kundenaktivitäten funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md).
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Rohdaten werden in Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md).
* [Bekanntes Problem in Adobe Commerce 2.4.0: Schaltfläche &quot;Auswahl zum Warenkorb hinzufügen&quot;funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md).
