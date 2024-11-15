---
title: Bekanntes Problem beim Produktvergleich in Adobe Commerce 2.3.5
description: Dieser Artikel enthält Empfehlungen dazu, wie ein bekanntes [Produktvergleich](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/shopper-tools/product-compare)-Problem in Adobe Commerce vor Ort 2.3.5 und Adobe Commerce in Cloud-Infrastruktur 2.3.5 vermieden werden kann.
exl-id: 1488e2db-4a5d-4963-b48e-b84f760582d1
feature: Products, Storefront
role: Admin
source-git-commit: b3d39e6b02728f05f046adf7be94ffacbca944d5
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Bekanntes Problem beim Produktvergleich in Adobe Commerce 2.3.5

Dieser Artikel enthält Empfehlungen dazu, wie ein bekanntes [Produktvergleich](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/shopper-tools/product-compare)-Problem in Adobe Commerce vor Ort 2.3.5 und Adobe Commerce in der Cloud-Infrastruktur 2.3.5 vermieden werden kann.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.3.5
* Adobe Commerce in Cloud-Infrastruktur 2.3.5

## Problem

Wenn ein Benutzer versucht, Produkte aus verschiedenen Store-Ansichten zu vergleichen, und ein Produkt einen leeren Wert für ein vergleichbares Attribut hat, zeigt Adobe Commerce eine beschädigte Seite &quot;Produkte vergleichen&quot;an.

## Lösung

Geben Sie nicht leere Werte für vergleichbare Produktattribute an oder verwenden Sie den standardmäßigen Store-Ansichtswert für das Attribut. Vergleichbare Attributwerte dürfen nicht leer sein.

>[!NOTE]
>
>Produktattribute werden für den Vergleich mit der Konfigurationseinstellung **Vergleichbar auf der Storefront** festgelegt. Weitere Informationen finden Sie unter [Erstellen von Produktattributen](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create#step-4-describe-the-storefront-properties) in unserem Benutzerhandbuch.

In Adobe Commerce 2.3.6, das ab 4. Quartal 2020 veröffentlicht werden soll, ist eine Korrektur verfügbar.

Sie können die Fehlerbehebung in GitHub anzeigen (beachten Sie bitte, dass die Korrektur nicht durch Regressionstests durchgeführt wurde und kein offizieller Hotfix ist): <https://github.com/magento/magento2/pull/27662>

## Verwandtes Lesen

<ul><li>Knowledge Base-Artikel zur Adobe Commerce-Unterstützung für bekannte Probleme mit Adobe Commerce 2.3.5:<ul>
<li>
<p title="Multi-Versandaufträge mit einem virtuellen Produkt werden in Adobe Commerce 2.3.5 nicht korrekt verarbeitet"><a href="/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md">Multi-Versandaufträge mit einem virtuellen Produkt werden in Adobe Commerce 2.3.5 nicht korrekt verarbeitet</a></p>
</li>
<li><a href="/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md">Bekanntes Problem bei der Produktanzahl für Massenaktionen in Adobe Commerce 2.3.5</a></li>
<li>
<p title="Patch für Amazon Pay-out-Problem in Adobe Commerce 2.3.5-p1"><a href="/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md">Patch für Amazon Pay-out-Problem in Adobe Commerce 2.3.5-p1</a></p>
</li>
</ul>
</li><li><a href="https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues">Bekannte Probleme mit Adobe Commerce 2.3.5</a> in unserer Entwicklerdokumentation</li></ul>
