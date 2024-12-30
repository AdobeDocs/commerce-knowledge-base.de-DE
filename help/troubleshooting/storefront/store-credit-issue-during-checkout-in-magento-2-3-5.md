---
title: Speicherkreditproblem beim Checkout in Adobe Commerce 2.3.5
description: Dieser Artikel bietet eine Problemumgehung für das bekannte Problem mit dem Store-Guthaben beim Checkout in Adobe Commerce 2.3.5, bei dem Käufer beim Checkout Fehler erhalten, nachdem sie die Verwendung des Store-Guthabens ausgewählt und später entfernt haben. In Adobe Commerce 2.3.6 ist eine dauerhafte Fehlerbehebung verfügbar.
exl-id: a0cca226-4d95-40b3-bd37-f13d28591366
feature: Checkout, Orders, Storefront
role: Admin
source-git-commit: b3d39e6b02728f05f046adf7be94ffacbca944d5
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---

# Speicherkreditproblem beim Checkout in Adobe Commerce 2.3.5

Dieser Artikel bietet eine Problemumgehung für das bekannte Problem mit dem Store-Guthaben beim Checkout in Adobe Commerce 2.3.5, bei dem Käufer beim Checkout Fehler erhalten, nachdem sie die Verwendung des Store-Guthabens ausgewählt und später entfernt haben. In Adobe Commerce 2.3.6 ist eine dauerhafte Fehlerbehebung verfügbar.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.3.5
* Adobe Commerce auf Cloud-Infrastruktur 2.3.5

## Problem

<u>Schritte zur Reproduktion</u>:

1. Der Kunde fügt Produkte zum Warenkorb hinzu und geht zur Kasse.
1. Kunde gibt „Gutschrift speichern“ als Zahlungsmethode an.
1. Der Kunde entfernt das Speicherguthaben und ändert die Zahlungsmethode.
1. Der Kunde geht durch den Checkout vor.

<u>Erwartete Ergebnisse</u>:

Alle Bestellinformationen werden korrekt angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Adobe Commerce gibt auf der Bestellseite im Abschnitt „Bestellzusammenfassung“ einen Fehler aus.

## Lösung

Kunden können die Seite „Bestellung“ aktualisieren, und die Informationen in der Bestellübersicht werden korrekt geladen. Eine Fehlerbehebung wird in Adobe Commerce 2.3.6 verfügbar sein, die im 4. Quartal 2020 veröffentlicht werden soll.

## Verwandtes Lesen

Artikel zu Adobe Commerce 2.3.5 Bekannte Probleme in unserer Support-Wissensdatenbank:

* [Mehrfach versendete Bestellungen mit einem virtuellen Produkt werden in Adobe Commerce 2.3.5 nicht korrekt verarbeitet](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)

* [Bekanntes Problem mit der Produktzahl für Massenaktionen in Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)

* [Patch für das Problem mit der gebührenpflichtigen Kasse von Amazon in Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)

* [Problem mit dem Produktvergleich in Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)

In unserer Entwicklerdokumentation:

* [Bekannte Probleme mit Adobe Commerce 2.3.5](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
