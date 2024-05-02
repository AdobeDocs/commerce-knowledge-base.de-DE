---
title: "MDVA-29400: Duplizierte Bestellungen bei PayPal Express Checkout"
description: Der Patch MDVA-29400 löst das Problem, dass duplizierte Bestellungen erstellt werden, wenn Kunden mit PayPal Express Checkout Bestellungen aufgeben. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-29400. Beachten Sie, dass das Problem in Adobe Commerce 2.4.1 behoben wurde.
exl-id: 75b943c8-5f7c-4d94-ae92-935428fdfcf8
feature: Checkout, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-29400: Doppelte Bestellungen bei PayPal Express Checkout

Der Patch MDVA-29400 löst das Problem, dass duplizierte Bestellungen erstellt werden, wenn Kunden mit PayPal Express Checkout Bestellungen aufgeben. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 ist installiert. Die Patch-ID lautet MDVA-29400. Beachten Sie, dass das Problem in Adobe Commerce 2.4.1 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Duplizierte Bestellungen werden erstellt, wenn Benutzer Bestellungen mit PayPal Express Checkout aufgeben.

<u>Voraussetzungen</u>:

PayPal Express-Checkout aktiviert und konfiguriert.

<u>Zu reproduzierende Schritte</u>:

1. Produkt zum Warenkorb hinzufügen.
1. Gehen Sie zur Checkout-Seite und verwenden Sie PayPal Express als Zahlungsmethode.
1. Sie wird zur Seite &quot;paypal/Express/review/&quot;umgeleitet.
1. Bestellung aufgeben Sie werden auf die Erfolgsseite weitergeleitet.
1. Gehen Sie zurück zu PayPal/Express/review/ Seite.
1. Klicken Sie auf **Bestellung platzieren** Schaltfläche.

<u>Erwartete Ergebnisse</u>:

Es wird nur eine Bestellung erstellt.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten den folgenden Fehler: *PayPal Express Checkout-Token gibt es nicht*, aber die zweite Bestellung wurde erfolgreich platziert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) Abschnitt.
