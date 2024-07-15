---
title: Adobe Commerce fordert Kunden auf, sich über einen ungültigen Link anzumelden
description: Der Artikel enthält einen Link zum Patch für ein bekanntes Adobe Commerce 2.3.5-Problem, bei dem Kunden aufgefordert werden, sich anzumelden, der Link zum erneuten Senden einer Bestätigungs-E-Mail jedoch nicht funktioniert.
exl-id: 8adef44f-56a6-4f57-a9b5-fb8583d8ae8d
feature: Logs
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Adobe Commerce fordert Kunden auf, sich über einen ungültigen Link anzumelden

Der Artikel enthält einen Link zum Patch für ein bekanntes Adobe Commerce 2.3.5-Problem, bei dem Kunden aufgefordert werden, sich anzumelden, der Link zum erneuten Senden einer Bestätigungs-E-Mail jedoch nicht funktioniert.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5

## Problem

Adobe Commerce fordert Kunden auf, sich mit der folgenden Meldung anzumelden: *&quot;Dieses Konto wird nicht bestätigt. Klicken Sie hier , um die Bestätigungs-E-Mail &quot;* erneut zu senden. Der Link **Hier klicken** sollte die Seite mit dem Link zur Bestätigung des Versands öffnen, ist jedoch inaktiv.

## Lösung

Ein Patch für dieses Problem ist in den technischen Ressourcen von Adobe Commerce verfügbar: [Patch zur Bestätigung des E-Mail-Links zur Kontobestätigung erneut senden für Adobe Commerce 2.3.5](https://magento.com/tech-resources/download?_ga=2.193540264.409362045.1590506265-807369446.1578680711#download2368). In Adobe Commerce 2.3.6, das ab 4. Quartal 2020 veröffentlicht werden soll, wird eine permanente Korrektur verfügbar sein.

Anweisungen zum Anwenden eines Composer-Patches finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches.

## Verwandtes Lesen

Artikel in unserer Support-Wissensdatenbank und Entwicklerdokumentation für bekannte Probleme mit Adobe Commerce 2.3.5:

* [Bekanntes Problem mit Adobe Commerce 2.3.5: Multi-ship-Bestellungen für virtuelle Produkte](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)
* [Bekanntes Problem beim Produktvergleich in Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
* [Adobe Commerce 2.3.5, 2.3.5-p1-Patch: Problem mit Länderzahlungen](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)
* [Adobe Commerce fordert Kunden auf, sich über einen ungültigen Link anzumelden](/help/troubleshooting/known-issues-patches-attached/magento-prompts-customers-log-in-invalid-link.md)
* [Bekanntes Problem bei der Produktanzahl für Massenaktionen in Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)
* [Patch für Amazon Pay-out-Problem in Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)
* [Bekannte Probleme mit Adobe Commerce 2.3.5](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
