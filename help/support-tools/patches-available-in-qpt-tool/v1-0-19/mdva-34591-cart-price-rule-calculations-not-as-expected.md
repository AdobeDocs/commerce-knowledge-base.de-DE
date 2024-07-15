---
title: "MDVA-34591: Berechnungen der Warenkorbpreisregel nicht wie erwartet"
description: Der Patch MDVA-34591 behebt das Problem, dass die Regel für den Warenkorbpreis mit **Höchster Mengenrabatt** nicht richtig funktioniert, wenn mehrere Regeln für Warenkorbpreise angewendet werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 installiert ist. Die Patch-ID lautet MDVA-34591. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.
exl-id: 1fa196bb-aab1-4364-a1b0-7c31d6d27d6d
feature: Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# MDVA-34591: Berechnungen der Warenkorbpreisregel nicht wie erwartet

Der Patch MDVA-34591 behebt das Problem, dass die Regel zum Warenkorbpreis mit **maximaler Mengenrabatt auf** nicht richtig angewendet wird, wenn mehrere Regeln zum Warenkorbpreis angewendet werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 installiert ist. Die Patch-ID lautet MDVA-34591. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.3.6

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce vor Ort und Adobe Commerce über Cloud-Infrastruktur 2.3.0-2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zum Admin und erstellen Sie die folgenden beiden Regeln:

   * Regel 1: 10 USD aus maximal drei Artikeln im Warenkorb. Legen Sie Priorität = *3* fest.
   * Regel 2: 50 % aller Produkte im Warenkorb. Legen Sie Priorität = *1* fest.

1. Gehen Sie zur Storefront.

1. Fügen Sie dem Warenkorb acht Mengen eines Produktes hinzu, die auf Preis = *$51* festgelegt sind.

1. Überprüfen Sie den Rabattbetrag im Warenkorb.

<u>Erwartete Ergebnisse</u>:

Der berechnete Rabatt beträgt erwartungsgemäß 234 USD.

* Berechnungen:

  Entsprechende Regeln für den Warenkorbpreis: Regel 2, Regel 1\
  Regel 2 anwenden (50 % Rabatt), also Rabatt = 204 USD\
  Regel 1 anwenden (10 von 3 Elementen), also Rabatt = 30 USD\
  Rabatt insgesamt = MIN ( 408/2 + 10x3, 8 &#42; 51) = MIN (204 + 30, 8 &#42; 51) = 234 USD

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt wird fälschlicherweise auf 153 USD berechnet, was auf die falsche Menge zurückzuführen ist, die zur Berechnung des maximalen Rabattwerts verwendet wird, da der feste Rabattbetrag unabhängig vom Betrag der Produkte im Warenkorb angewendet wird.

* Berechnungen:

  Entsprechende Regeln für den Warenkorbpreis: Regel 2, Regel 1\
  Regel 2 anwenden (50 % Rabatt), also Rabatt = 204 USD\
  Regel 1 anwenden (10 von 3 Elementen), also Rabatt = 30 USD\
  Rabatt insgesamt = MIN (204 + 30, 3 &#42; 51) = 153 USD

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) verfügbare Patches.
