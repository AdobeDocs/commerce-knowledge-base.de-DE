---
title: 'Adobe Commerce 2.4.0: 404-Fehler beim Entfernen von Belohnungspunkten beim Multi-Shipping-Checkout'
description: Dieser Artikel bietet eine Problemumgehung für ein bekanntes Problem in Adobe Commerce 2.4.0 im Zusammenhang mit dem Fehler „404 Not Found*" auf einer Web-Seite beim Entfernen von Belohnungspunkten auf einer Kasse mit mehreren Sendungen. Derzeit wird auf der Multi-Shipping-Checkout-Seite beim Versuch, Belohnungspunkte zu entfernen, mit denen für eine Bestellung bezahlt wurde, eine Seite "*404 Nicht gefunden* " anstelle der erfolgreichen Stornierung von Belohnungspunkten angezeigt. Dieses Problem wird in mit einer Adobe Commerce-Patch-Version 2.4.1 behoben.
exl-id: 59de4b3d-af28-4ae8-8f55-4ec958e6ee8b
feature: B2B, Checkout, Orders, Rewards, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: 404-Fehler beim Entfernen von Belohnungspunkten beim Multi-Shipping-Checkout

Dieser Artikel bietet eine Problemumgehung für ein bekanntes Problem in Adobe Commerce 2.4.0 im Zusammenhang mit einem Webseitenfehler &quot;*404 Not Found* beim Entfernen von Belohnungspunkten auf einer mehrversandten Checkout-Seite. Derzeit wird auf der Multi-Shipping-Checkout-Seite beim Versuch, Belohnungspunkte zu entfernen, mit denen für eine Bestellung bezahlt wurde, eine Seite &quot;*404 Nicht gefunden* &quot; anstelle der erfolgreichen Stornierung der Belohnungspunkte angezeigt. Dieses Problem wird in mit einer Adobe Commerce-Patch-Version 2.4.1 behoben.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.0 (alle Bereitstellungsmethoden)

## Problem

<u>Schritte zur Reproduktion</u>

1. Navigieren Sie zur Storefront und melden Sie sich als Kunde an.
1. Fügen Sie mindestens zwei Produkte zum **Warenkorb“**.
1. Öffnen Sie den **Mini-Warenkorb**.
1. Klicken Sie auf den **Warenkorb anzeigen und bearbeiten**.
1. Klicken Sie auf den **Auschecken mit mehreren**).
1. Wählen Sie Versandadressen auf der Seite **Versand an mehrere Adressen**.
1. Klicken Sie auf die **Zu Versandinformationen wechseln**.
1. Wählen Sie für **Adresse die Option „Flatrate - Feste**&quot; aus.
1. Klicken Sie auf **Schaltfläche „Weiter zu Rechnungsinformationen**.
1. Aktivieren Sie das **Belohnungspunkte verwenden** auf der Seite **Rechnungsinformationen**.
1. Klicken Sie auf die **Zum Überprüfen Ihrer Bestellung wechseln**.
1. Klicken Sie auf den **Entfernen**-Link für eine beliebige Adresse, um die Belohnungspunkte zu entfernen.

<u>Erwartete Ergebnisse</u>

* Die **Warenkorb** sollte angezeigt werden.
* Die &quot;*Sie haben die Belohnungspunkte aus dieser Bestellung entfernt.*&quot; sollte angezeigt werden.

<u>Tatsächliches Ergebnis</u>

Die Fehlerseite &quot;*404 Not*&quot; wird angezeigt.

## Abhilfe

Die Problemumgehung besteht darin, den Käufer zurück zum **Warenkorb** navigieren zu lassen und die Belohnungspunkte von der **Warenkorb**-Webseite zu entfernen. Das Problem wird voraussichtlich mit dem Patch der Adobe Commerce-Version 2.4.1 behoben, der im 4. Quartal 2020 veröffentlicht werden soll.

## Verwandtes Lesen

* [Bekanntes Problem in Adobe Commerce 2.4.0 - Aktualisierung der Aktivitäten des Kunden funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Rohnachrichtendaten werden in der Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B-Admin kann kein konfigurierbares Produkt zum Angebot hinzufügen](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Fehler bei der Anzeige von Bestellungen](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
