---
title: "MDVA-33559 Patch: PayflowPro payment denied error"
description: Der Patch MDVA-33559 löst das Problem, dass PayPal PayflowPro Zahlungen abgelehnt werden.
exl-id: aec57ffa-07c7-404e-985d-8ec4fdb019b1
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# MDVA-33559 Patch: PayflowPro-Zahlung abgelehnt Fehler

Der Patch MDVA-33559 löst das Problem, dass PayPal PayflowPro Zahlungen abgelehnt werden.

Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p2

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.0 - 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Problem betrifft die Sonderzeichen für das kaufmännische Und-Zeichen (&amp;) und Gleichheitszeichen (=), die in Namen verwendet werden.

<u>Zu reproduzierende Schritte</u>:

1. Fügen Sie dem Warenkorb ein einfaches Produkt hinzu.
1. Gehen Sie zum Checkout.
1. Legen Sie die Lieferadresse fest. (Beispiel einer Versandadresse: **Vorname** = ** *John&#39;s* **  **Nachname** = ** *Äpfel &amp; Orange, Inc* **  **Straße** = *1234 E Nameless St.*  **Land** = *USA*  **Bundesland/Provinz** = *Anystate*  **Ort** = *Anytown*  **Zip** = *12345*  **Telefon** = *1234567890*)
1. Legen Sie die Zahlung auf **PayPal PayflowPro** und versuchen Sie, den Checkout abzuschließen.

<u>Erwartete Ergebnisse</u>:

Die Transaktion führt zu einer erfolgreichen Zahlung oder einer korrekten Fehlermeldung, wie erwartet.

<u>Tatsächliche Ergebnisse</u>:

Die Transaktion wird abgelehnt, und der Kunde erhält eine E-Mail mit der Meldung &quot;Transaktion wurde abgelehnt&quot;.

## Wenden Sie den Patch an

Verwenden Sie je nach Adobe Commerce-Produkt die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
