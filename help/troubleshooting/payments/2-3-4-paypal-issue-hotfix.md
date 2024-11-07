---
title: 2.3.4 PayPal-Problem Hotfix
description: Dieser Artikel enthält eine Fehlerbehebung für Fehler, die während der Bestellplatzierung bei der Auswahl einer Region in PayPal Express Checkout empfangen wurden. Das Problem wird durch Änderungen in der Adobe Commerce-Version 2.3.4 verursacht und hängt damit zusammen, wie die Adressfelder des PayPal Express Checkout analysiert werden.
exl-id: 9f5ec100-49b0-4ac5-8951-32b5c4fe6bed
feature: Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 2.3.4 PayPal-Problem Hotfix

Dieser Artikel enthält eine Fehlerbehebung für Fehler, die während der Bestellplatzierung bei der Auswahl einer Region in PayPal Express Checkout empfangen wurden. Das Problem wird durch Änderungen in der Adobe Commerce-Version 2.3.4 verursacht und hängt damit zusammen, wie die Adressfelder des PayPal Express Checkout analysiert werden.

## Betroffene Versionen und Produkte

* Adobe Commerce auf Cloud-Infrastruktur v2.3.4
* Adobe Commerce On-Premise v2.3.4

## Problem

Bei der Eingabe des Landes und der Region während der Bestellplatzierung in PayPal Express Checkout tritt ein Fehler auf. Das Problem ist reproduzierbar für jedes Land, in dem das Feld region im Adressbereich ein Textfeld ist (im Gegensatz zu einem Dropdown-Menü).

<u>Zu reproduzierende Schritte</u> :

1. Aktivieren Sie PayPal Express Checkout.
1. Fügen Sie ein Produkt zum Warenkorb als Gast oder bei der Anmeldung hinzu.
1. Gehen Sie zum Checkout.
1. Wählen Sie Ihre Versandadresse aus. Beispiel: *UK* . Geben Sie dann eine Eingabe in das Feld **Bundesland/-staat** ein. Beispiel: *Nottinghamshire*.
1. Klicken Sie auf die Schaltfläche **Bestellung platzieren** , um die Bestellung aufzugeben. Sie erhalten eine erfolgreiche Bestellseite und eine Bestätigungs-E-Mail.

<u>Erwartetes Ergebnis:</u>

Die Bestellung wurde erfolgreich platziert.

<u>Tatsächliches Ergebnis:</u>

Wenn auf die Bestellschaltfläche geklickt wird, wird ein Fehler angezeigt:

```
Error 500: NOTICE: PHP message: PHP Fatal error: Uncaught Error: Call to a member
  function getId() on null in httpdocs/vendor/magento/module-paypal/Model/Api/Nvp.php:1527
```

## Lösung

Bei lokalen Adobe Commerce-Händlern: Wenden Sie den Hotfix [, den Sie über das Portal [magento.com](https://magento.com) im Bereich Downloads unter Mein Konto finden.](https://magento.com/tech-resources/download#download2353)

Für Adobe Commerce für Cloud-Infrastruktur-Händler: Adobe hat die Fehlerbehebung in den Cloud-Patches für Commerce Version 1.0.2 enthalten. Anweisungen zum Anwenden des neuesten Pakets finden Sie in der Entwicklerdokumentation unter [Cloud-Patches für Commerce-Versionshinweise](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches?itm_source=devdocs&amp;itm_medium=quick_search&amp;itm_campaign=federated_search&amp;itm_term=cloud%20patche) .

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches in unserer Support-Wissensdatenbank.

## Verwandte Informationen

* [Versionsinformationen > Adobe Commerce 2.3.4 Versionshinweise > Wenden Sie das PayPal Express Checkout-Problem mit dem Regions-Patch für Adobe Commerce 2.3.4 an, um ein kritisches PayPal Express Checkout-Problem](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-4-commerce.html#apply-the-paypal-express-checkout-issue-with-region-patch-for-magento-234-to-address-a-critical-paypal-express-checkout-issue) in unserer Entwicklerdokumentation zu beheben.
