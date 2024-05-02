---
title: "Adobe Commerce 2.4.0: 404-Fehler Entfernung von Belohnungspunkten beim Checkout mit mehreren Sendungen"
description: Dieser Artikel bietet eine Behelfslösung für ein bekanntes Problem in Adobe Commerce 2.4.0 für einen Webseitenfehler "*404 nicht gefunden*", wenn Prämienpunkte auf einer Multi-Versandkosten-Seite entfernt werden. Zurzeit wird auf der Seite mit dem Checkout für mehrere Versandaktionen beim Versuch, Punkte zu entfernen, die zum Bezahlen einer Bestellung verwendet wurden, anstelle der erfolgreichen Stornierung von Belohnungspunkten eine Seite "*404 Not Found*"angezeigt. Dieses Problem wird mit einer Patch-Version von Adobe Commerce 2.4.1 in behoben.
exl-id: 59de4b3d-af28-4ae8-8f55-4ec958e6ee8b
feature: B2B, Checkout, Orders, Rewards, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: 404-Fehler Entfernung von Belohnungspunkten beim Multi-Shipping-Checkout

Dieser Artikel bietet eine Behelfslösung für ein bekanntes Problem in Adobe Commerce 2.4.0 für eine *404 nicht gefunden*&quot;Webseitenfehler beim Entfernen von Belohnungspunkten auf einer Checkout-Seite mit mehreren Sendungen. Derzeit wird auf der Seite mit dem Checkout für mehrere Sendungen beim Versuch, die Punkte zu entfernen, die zum Bezahlen einer Bestellung verwendet wurden, ein &quot;*404 nicht gefunden* &quot;anstelle der erfolgreichen Löschung von Belohnungspunkten angezeigt wird. Dieses Problem wird mit einer Patch-Version von Adobe Commerce 2.4.1 in behoben.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.0 (alle Bereitstellungsmethoden)

## Problem

<u>Zu reproduzierende Schritte</u>

1. Navigieren Sie zur Storefront und melden Sie sich als Kunde an.
1. Fügen Sie mindestens zwei Produkte zu **Warenkorb**.
1. Öffnen Sie die **Warenkorb**.
1. Klicken Sie auf **Warenkorb anzeigen und bearbeiten** -Link.
1. Klicken Sie auf **Mit mehreren Adressen auschecken** -Link.
1. Versandadressen auf der Seite **An mehrere Adressen senden** Seite.
1. Klicken Sie auf **Navigieren Sie zu Versandinformationen .** Schaltfläche.
1. Wählen Sie die **Pauschalsatz - Feste Versandmethode** für jede Adresse.
1. Klicken Sie auf **Weiter zu Rechnungsinformationen** Schaltfläche.
1. Überprüfen Sie die **Verwenden Sie Ihre Prämienpunkte** Kontrollkästchen auf der **Rechnungsinformationen** Seite.
1. Klicken Sie auf **Gehen Sie zu Bestellung überprüfen .** Schaltfläche.
1. Klicken Sie auf **Entfernen** -Link für jede Adresse, um die Belohnungspunkte zu entfernen.

<u>Erwartete Ergebnisse</u>

* Die **Warenkorb** angezeigt.
* Die &quot;*Sie haben die Belohnungspunkte aus dieser Bestellung entfernt.* angezeigt.

<u>Tatsächliches Ergebnis</u>

A *404 nicht gefunden* &quot; Fehlerseite angezeigt.

## Workaround

Die Lösung besteht darin, dass der Käufer zurück zum **Warenkorb** und die Belohnungspunkte aus der **Warenkorb** Webseite. Das Problem wird voraussichtlich im Patch der Adobe Commerce-Version 2.4.1 behoben, der für Q4 2020 geplant ist.

## Verwandtes Lesen

* [Bekanntes Problem mit Adobe Commerce 2.4.0 - Aktualisierung der Kundenaktivitäten funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Rohmeldungsdaten werden in Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B Admin kann kein konfigurierbares Produkt zum Anführungszeichen hinzufügen](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Fehler bei der Auftragsanzeige](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
