---
title: 'Adobe Commerce 2.4.0 Problem: Rohdaten der Storefront-Nachricht werden angezeigt'
description: Dieser Artikel bietet eine Lösung für das Problem, wenn alle Fehlermeldungen auf der Storefront mit einem "+"-Zeichen anstelle eines Leerzeichens angezeigt werden. Diese Lösung hilft, Fehlermeldungen lesbar zu halten.
exl-id: f44fe434-a320-4e7e-a876-9575921749f3
feature: Storefront
role: Admin
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 Problem: Rohdaten der Storefront-Nachricht werden angezeigt

Dieser Artikel bietet eine Lösung für das Problem, wenn alle Fehlermeldungen auf der Storefront mit einem &quot;+&quot;-Zeichen anstelle eines Leerzeichens angezeigt werden. Diese Lösung hilft, Fehlermeldungen lesbar zu halten.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.4.0
* Adobe Commerce On-Premises 2.4.0.

## Problem

<u>Schritte zur Reproduktion:</u>

1. Navigieren Sie **Seite „Neues Konto erstellen** in der Storefront.
1. Erstellen Sie mithilfe einer registrierten E-Mail ein neues Konto. Die folgende Meldung wird angezeigt:

`There+is+already+an+account+with+this+email+address.+If+you+are+sure+that+it+is+your+email+address,+click+here+to+get+your+password+and+access+your+account.`

## Ursache

Das Problem wird durch ein PHP 7.4.2-Problem im Zusammenhang mit set\\read Cookies verursacht. Siehe [PHP BUG \#79174 setcookie() kodiert Leerzeichen als \`+\`, aber $\_COOKIE dekodiert sie nicht mehr](https://bugs.php.net/bug.php?id=79174).

## Lösung

Um dieses Problem zu lösen, verwenden Sie eine andere Version von PHP 7.4.x. PHP 7.4.2 wird von Adobe Commerce 2.4.0 nicht unterstützt.

## Weiterführende Informationen finden Sie in unserer Support-Wissensdatenbank:

* [Commerce 2.4.0 Bekanntes Problem: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Aktualisierung der Aktivitäten des Kunden funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Die Schaltfläche „Auswahl zu meinem Warenkorb hinzufügen“ funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
