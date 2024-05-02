---
title: "Adobe Commerce 2.4.0-Ausgabe: Anzeige von Storefront-Rohmeldungsdaten"
description: Dieser Artikel bietet eine Lösung für das Problem, dass alle Fehlermeldungen auf der Storefront mit einem "+"-Zeichen anstelle eines Leerzeichens angezeigt werden. Diese Lösung hilft dabei, Fehlermeldungen lesbar zu halten.
exl-id: f44fe434-a320-4e7e-a876-9575921749f3
feature: Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Problem mit Adobe Commerce 2.4.0: Anzeige von Storefront-Rohmeldungsdaten

Dieser Artikel bietet eine Lösung für das Problem, dass alle Fehlermeldungen auf der Storefront mit einem &quot;+&quot;-Zeichen anstelle eines Leerzeichens angezeigt werden. Diese Lösung hilft dabei, Fehlermeldungen lesbar zu halten.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.4.0
* Adobe Commerce vor Ort 2.4.0.

## Problem

<u>Zu reproduzierende Schritte:</u>

1. Navigieren Sie zu **Neues Konto erstellen** auf der Storefront angezeigt.
1. Erstellen Sie ein neues Konto mit einer registrierten E-Mail. Die folgende Meldung wird angezeigt:

`There+is+already+an+account+with+this+email+address.+If+you+are+sure+that+it+is+your+email+address,+click+here+to+get+your+password+and+access+your+account.`

## Ursache

Das Problem wird durch ein PHP 7.4.2-Problem verursacht, das sich auf set\\read-Cookies bezieht. Siehe [PHP BUG \#79174 setcookie() kodiert Leerzeichen als \`+\`, aber $\_COOKIE dekodiert sie nicht mehr](https://bugs.php.net/bug.php?id=79174).

## Lösung

Um dieses Problem zu lösen, verwenden Sie eine andere Version von PHP 7.4.x. PHP 7.4.2 wird von Adobe Commerce 2.4.0 nicht unterstützt.

## Verwandte Lesungen in unserer Wissensdatenbank:

* [Bekanntes Problem in Commerce 2.4.0: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekanntes Problem bei der Erstellung von Versandbeschriftungen in Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Aktualisierung der Kundenaktivitäten funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Schaltfläche &quot;Auswahl zum Warenkorb hinzufügen&quot;funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
