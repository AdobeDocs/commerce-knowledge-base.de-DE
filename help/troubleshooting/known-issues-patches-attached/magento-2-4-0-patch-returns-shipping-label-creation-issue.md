---
title: 'Adobe Commerce 2.4.0 Patch: gibt Problem bei der Erstellung von Versandbeschriftungen zurück.'
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.4.0-Problem, wenn beim Drucken einer Versandbeschriftung für die Rückgaben von Kunden Probleme auftreten.
exl-id: f78f8d7e-29e9-4d6c-83f6-cd5afa1d7d9c
feature: B2B, Orders, Returns, Communications, Shipping/Delivery
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Adobe Commerce 2.4.0-Patch: gibt Problem bei der Erstellung von Versandbeschriftungen zurück

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.4.0-Problem, wenn beim Drucken einer Versandbeschriftung für die Rückgaben von Kunden Probleme auftreten.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.4.0
* Adobe Commerce vor Ort 2.4.0

## Problem

<u>Zu reproduzierende Schritte:</u>

1. Positionieren Sie eine Bestellung bei einer der folgenden Hauptversandmethoden: FedEx, DHL, UPS und USPS.
1. Erstellen und autorisieren Sie die Rückgaben für diese Bestellung.
1. Öffnen Sie eine autorisierte Seite **Rückgabeinformationen** und klicken Sie auf die Schaltfläche **Versandtitel erstellen** .
1. Wählen Sie Versandmethode aus, fügen Sie ein Produkt zu einem Paket hinzu und klicken Sie auf Speichern.

<u>Erwartetes Ergebnis:</u>

Eine Versandbeschriftung wurde erfolgreich erstellt und Sie sehen eine Meldung: *Sie haben einen Versandtitel erstellt.*

<u>Tatsächliches Ergebnis:</u>

Die Seite **Rückkehrinformationen** ist beschädigt und auf der Seite &quot;Rückkehrinformationen&quot;wird eine Fehlermeldung angezeigt: *Allgemeine Informationsänderungen wurden an diesem Abschnitt vorgenommen, die nicht gespeichert wurden. Diese Registerkarte enthält ungültige Daten*.

## Lösung

Wenden Sie den in diesem Artikel angegebenen [Patch](assets/MC-35984-2.4.0-CE-composer.patch.zip) an.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MC-35984-2.4.0-CE-composer.patch](assets/MC-35984-2.4.0-CE-composer.patch.zip)

Der Patch kann auch in den Formaten `.git` und `.composer` heruntergeladen werden, und zwar auf der Seite [Adobe Commerce-Downloads](https://magento.com/tech-resources/download) unter **Patches** in der linken Spaltennavigation. Suchen Sie nach dem Patch MC-35984 .

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches auf unserer Support-Wissensseite.

## Verwandte Lesungen in unserer Wissensdatenbank:

* [Bekanntes Problem mit Adobe Commerce 2.4.0: Rohdaten werden in Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Schaltfläche &quot;Auswahl zum Warenkorb hinzufügen&quot;funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0 B2B Admin kann kein konfigurierbares Produkt zum Anführungszeichen hinzufügen](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Bestellungen zeigen Fehler an](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
