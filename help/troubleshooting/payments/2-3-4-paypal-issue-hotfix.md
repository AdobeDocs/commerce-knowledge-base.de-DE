---
title: 2.3.4 Hotfix für PayPal-Probleme
description: Dieser Artikel bietet eine Fehlerbehebung für Fehler, die bei der Bestellplatzierung bei der Auswahl einer Region in der PayPal Express-Checkout empfangen wurden. Das Problem wird durch Änderungen in der Adobe Commerce-Version 2.3.4 verursacht und hängt damit zusammen, wie die Adressfelder des PayPal Express-Checkouts geparst werden.
exl-id: 9f5ec100-49b0-4ac5-8951-32b5c4fe6bed
feature: Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 2.3.4 Hotfix für PayPal-Probleme

Dieser Artikel bietet eine Fehlerbehebung für Fehler, die bei der Bestellplatzierung bei der Auswahl einer Region in der PayPal Express-Checkout empfangen wurden. Das Problem wird durch Änderungen in der Adobe Commerce-Version 2.3.4 verursacht und hängt damit zusammen, wie die Adressfelder des PayPal Express-Checkouts geparst werden.

## Betroffene Versionen und Produkte

* Adobe Commerce auf Cloud-Infrastruktur v2.3.4
* Adobe Commerce On-Premise v2.3.4

## Problem

Bei der Eingabe des Landes und der Region während der Bestellplatzierung im PayPal Express-Checkout tritt ein Fehler auf. Das Problem kann in jedem Land reproduzierbar sein, in dem das Feld Region im Abschnitt Adresse ein Textfeld ist (im Gegensatz zu einem Dropdown-Menü).

<u>Schritte zur Reproduktion</u> :

1. PayPal Express-Checkout aktivieren.
1. Fügen Sie das Produkt als Gast oder bei der Anmeldung zum Warenkorb hinzu.
1. Zur Kasse gehen.
1. Wählen Sie Ihre Versandadresse aus. Beispiel: *UK* . Geben Sie dann eine Eingabe in das Feld **Bundesland/**&quot; ein. Beispiel: *Nottinghamshire*.
1. Klicken Sie auf die Schaltfläche **Bestellung aufgeben**, um eine Bestellung aufzugeben. Sie erhalten eine erfolgreiche Bestellseite und eine Bestätigungs-E-Mail.

<u>Erwartetes Ergebnis:</u>

Die Bestellung wurde erfolgreich aufgegeben.

<u>Tatsächliches Ergebnis:</u>

Wenn auf die Schaltfläche „Bestellung“ geklickt wird, wird ein Fehler angezeigt:

```
Error 500: NOTICE: PHP message: PHP Fatal error: Uncaught Error: Call to a member
  function getId() on null in httpdocs/vendor/magento/module-paypal/Model/Api/Nvp.php:1527
```

## Lösung

Für lokale Adobe Commerce-Händler: Wenden Sie den [Hotfix](https://magento.com/tech-resources/download#download2353) an, der im Abschnitt Downloads auf dem Portal [magento.com](https://magento.com) in Mein Konto verfügbar ist.

Für Händler mit Adobe Commerce-Cloud-Infrastruktur: Adobe hat die Fehlerbehebung in die Cloud-Patches für Commerce v1.0.2 aufgenommen. Siehe [Cloud-Patches für Commerce](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches?itm_source=devdocs&amp;itm_medium=quick_search&amp;itm_campaign=federated_search&amp;itm_term=cloud%20patche) in unserer Entwicklerdokumentation, um Anweisungen zum Anwenden des neuesten Pakets zu erhalten.

## Anwenden des Patches

Anweisungen finden Sie unter [So wenden Sie einen von Adobe bereitgestellten Composer-Patch ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) unserer Support-Wissensdatenbank an.

## Verwandtes Lesen

* [Versionshinweise > Adobe Commerce 2.3.4 Versionshinweise > Wenden Sie das Problem mit dem PayPal Express-Checkout mit dem Regionen-Patch für Adobe Commerce 2.3.4 an, um ein wichtiges Problem mit dem PayPal Express-Checkout zu beheben](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-4-commerce.html#apply-the-paypal-express-checkout-issue-with-region-patch-for-magento-234-to-address-a-critical-paypal-express-checkout-issue) in unserer Entwicklerdokumentation.
