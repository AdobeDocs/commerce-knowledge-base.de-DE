---
title: Kreditausfall beim Checkout in Adobe Commerce 2.3.5
description: Dieser Artikel bietet eine Problemumgehung für das bekannte Problem, das beim Checkout in Adobe Commerce 2.3.5 mit Store-Gutschriften in Zusammenhang steht und bei dem Käufer beim Checkout nach Auswahl und späterer Entfernung der Nutzung von Store-Gutschriften Fehler erhalten. In Adobe Commerce 2.3.6 wird eine permanente Korrektur verfügbar sein.
exl-id: a0cca226-4d95-40b3-bd37-f13d28591366
feature: Checkout, Orders, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Kreditausfall beim Checkout in Adobe Commerce 2.3.5

Dieser Artikel bietet eine Problemumgehung für das bekannte Problem, das beim Checkout in Adobe Commerce 2.3.5 mit Store-Gutschriften in Zusammenhang steht und bei dem Käufer beim Checkout nach Auswahl und späterer Entfernung der Nutzung von Store-Gutschriften Fehler erhalten. In Adobe Commerce 2.3.6 wird eine permanente Korrektur verfügbar sein.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.3.5
* Adobe Commerce in Cloud-Infrastruktur 2.3.5

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Der Kunde fügt Produkte zum Warenkorb hinzu und fährt mit dem Checkout fort.
1. Der Kunde gibt die Store-Gutschrift als Zahlungsmethode an.
1. Der Kunde entfernt die Gutschrift für den Store und ändert die Zahlungsmethode.
1. Der Kunde fährt mit dem Checkout fort.

<u>Erwartete Ergebnisse</u>:

Alle Bestellinformationen werden korrekt angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Adobe Commerce gibt im Abschnitt &quot;Bestellübersicht&quot;der Bestellseite einen Fehler aus.

## Lösung

Kunden können die Bestellseite aktualisieren. Die Informationen in der Bestellübersicht werden korrekt geladen. In Adobe Commerce 2.3.6, das ab 4. Quartal 2020 veröffentlicht werden soll, ist eine Korrektur verfügbar.

## Verwandtes Lesen

Artikel zu bekannten Problemen mit Adobe Commerce 2.3.5 in unserer Support-Wissensdatenbank:

* [Multi-Versandaufträge mit einem virtuellen Produkt werden in Adobe Commerce 2.3.5 nicht korrekt verarbeitet](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)

* [Ausgabe der Zahlungsmethode in Adobe Commerce auf Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.5 und 2.3.5-p1](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)

* [Adobe Commerce fordert Kunden auf, sich anzumelden, stellt jedoch einen ungültigen Link bereit](/help/troubleshooting/known-issues-patches-attached/magento-prompts-customers-log-in-invalid-link.md)

* [Bekanntes Problem bei der Produktanzahl für Massenaktionen in Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)

* [Patch für Amazon Pay-out-Problem in Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)

* [Produktvergleichsfehler in Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)

In unserer Entwicklerdokumentation:

* [Bekannte Probleme mit Adobe Commerce 2.3.5](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
