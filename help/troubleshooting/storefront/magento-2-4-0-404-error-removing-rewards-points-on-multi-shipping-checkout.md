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

Dieser Artikel bietet eine Behelfslösung für ein bekanntes Problem in Adobe Commerce 2.4.0 für einen &quot;*404 Not Found*&quot;-Webseitenfehler, wenn Belohnungspunkte auf einer Checkout-Seite mit mehreren Sendungen entfernt werden. Zurzeit wird auf der Seite mit dem Checkout für mehrere Versandkosten beim Versuch, Punkte zu entfernen, die zum Bezahlen einer Bestellung verwendet wurden, anstelle der erfolgreichen Löschung von Belohnungspunkten eine Seite &quot;*404 Not Found* &quot;angezeigt. Dieses Problem wird mit einer Patch-Version von Adobe Commerce 2.4.1 in behoben.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.0 (alle Bereitstellungsmethoden)

## Problem

<u>Zu reproduzierende Schritte</u>

1. Navigieren Sie zur Storefront und melden Sie sich als Kunde an.
1. Fügen Sie mindestens zwei Produkte zum **Warenkorb** hinzu.
1. Öffnen Sie den **Mini-Warenkorb**.
1. Klicken Sie auf den Link **Warenkorb anzeigen und bearbeiten** .
1. Klicken Sie auf den Link **Mit mehreren Adressen auschecken** .
1. Wählen Sie auf der Seite **An mehrere Adressen senden** Versandadressen aus.
1. Klicken Sie auf die Schaltfläche **Zu Versandinformationen wechseln** .
1. Wählen Sie für jede Adresse die Option **Pauschalrate - Feste Versandmethode** aus.
1. Klicken Sie auf die Schaltfläche **Weiter zu Rechnungsinformationen** .
1. Aktivieren Sie das Kontrollkästchen **Use Your Rewards Points** auf der Seite **Rechnungsinformationen** .
1. Klicken Sie auf die Schaltfläche **Gehe zu Bestellung überprüfen** .
1. Klicken Sie auf den Link **Entfernen** für eine beliebige Adresse, um die Belohnungspunkte zu entfernen.

<u>Erwartete Ergebnisse</u>

* Die Seite **Warenkorb** sollte angezeigt werden.
* Der &quot;*Sie haben die Belohnungspunkte aus dieser Bestellung entfernt.*&quot; angezeigt.

<u>Tatsächliches Ergebnis</u>

Die Fehlerseite &quot;*404 Not Found*&quot; wird angezeigt.

## Workaround

Die Lösung besteht darin, dass der Käufer zurück zum **Warenkorb** navigiert und die Belohnungspunkte von der Webseite **Warenkorb** entfernt. Das Problem wird voraussichtlich im Patch der Adobe Commerce-Version 2.4.1 behoben, der für Q4 2020 geplant ist.

## Verwandtes Lesen

* [Bekanntes Problem mit Adobe Commerce 2.4.0 - Aktualisierung der Kundenaktivitäten funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Rohmeldungsdaten werden in Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B Admin kann kein konfigurierbares Produkt zum Anführungszeichen hinzufügen](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Fehler bei der Auftragsanzeige](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
