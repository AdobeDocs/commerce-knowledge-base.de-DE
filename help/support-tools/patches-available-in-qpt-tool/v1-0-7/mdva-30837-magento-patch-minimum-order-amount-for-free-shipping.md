---
title: "MDVA-30837: Mindestbestellbetrag für kostenlosen Versand"
description: Der Patch MDVA-30837 fügt Konfigurationsoptionen für die kostenlose Versandberechnung hinzu, sodass der Benutzer den Mindestbestellbetrag so konfigurieren kann, dass er kostenlosen Versand auf Grundlage der Zwischensumme (oder Gesamtsumme) erhält. Dies ermöglicht lokale Anpassungen für Steuer- und Versandmethoden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
exl-id: 64716d08-4ce0-40d5-aeb7-242e2aa85bb0
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---

# MDVA-30837: Mindestbestellbetrag für kostenlosen Versand

Der Patch MDVA-30837 fügt Konfigurationsoptionen für die kostenlose Versandberechnung hinzu, sodass der Benutzer den Mindestbestellbetrag so konfigurieren kann, dass er kostenlosen Versand auf Grundlage der Zwischensumme (oder Gesamtsumme) erhält. Dies ermöglicht lokale Anpassungen für Steuer- und Versandmethoden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf Cloud-Infrastruktur 2.3.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce auf Cloud-Infrastruktur 2.3.1 - 2.3.4 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Patch MDVA-30837 fügt die Konfigurationseinstellung hinzu, um die Einstellung **Mindestbestellbetrag** so zu konfigurieren, dass der kostenlose Versand auf Grundlage der Zwischensumme (oder Gesamtsumme) erfolgt:

* **Steuern auf Betrag einbeziehen**: *Ja/Nein* in der Konfiguration der Versandmethode für kostenlosen Versand.
   * Wenn **Steuern auf Betrag einschließen** auf *Ja* gesetzt ist, wird der Mindestbestellbetrag als Zwischensumme + Steuer - Rabatt berechnet.
   * Wenn **Steuern auf Betrag einschließen** auf *NEIN* gesetzt ist, wird der Mindestbestellbetrag als Zwischensumme - Rabatt berechnet.

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Steuern** und legen Sie Folgendes fest:

   * Steuerberechnung basierend auf *Versandadresse*
   * Grenzüberschreitenden Handel aktivieren: *Nein*
   * Anzeigen von Produktionspreisen im Katalog: *ohne Steuern*
   * Versandpreise anzeigen: *ohne Steuern*
   * Anzeigepreise: *ohne Steuern*
   * Zwischensumme anzeigen: *Steuern ausschließen*
   * Versandbetrag anzeigen: *Ausschließen der Steuer*
   * Anzeige der Geschenkverpackungspreise: *ohne Steuern*
   * Anzeigen der gedruckten Kartenpreise: *ohne Steuern*
   * Steuern in Bestellsumme einbeziehen: *Ja*
   * Vollständige Steuerzusammenfassung anzeigen: *Ja*

1. Wechseln Sie zu **Umsatz** > **Versandeinstellungen** > **Kostenloses Versand** und legen Sie den Mindestbestellbetrag **7} = *30* fest.**
1. Gehen Sie zu **Marketing** > Promotions > **Regeln zum Warenkorbpreis** und erstellen Sie eine neue Preisregel (detaillierte Schritte finden Sie unter [Erstellen einer Preisregel für Warenkorb](https://docs.magento.com/user-guide/marketing/price-rules-cart-create.html) in unserem Benutzerhandbuch).

   * Couponcode = *spezifischer Coupon*.
   * Bedingungen: Zwischensumme größer/gleich 25 USD.
   * Aktionen: Kostenloser Versand = *Für Sendungen mit übereinstimmenden Artikeln*.

1. Erstellen Sie ein Produkt mit einem Preis von 23,10 USD.
1. Fügen Sie die CA-Steuer zur Standardsteuerregel hinzu.
1. Fügen Sie dieses Produkt zum Warenkorb hinzu.
1. Erhalten Sie einen Lieferpreis - nach Steuern, die Gesamtsumme = 25,01 USD und kostenloser Versand.
1. Anwenden des Gutscheincodes - dieser ist nicht gültig, da die Zwischensumme (ohne Steuern) 23,10 USD beträgt.

<u>Erwartete Ergebnisse</u>:

Es gibt eine zusätzliche Konfigurationseinstellung - &quot;Steuern auf Betrag einbeziehen&quot;: *Ja*/*Nein* in der Konfiguration der kostenlosen Versandmethode:

* Wenn &quot;Steuern auf Betrag einschließen&quot;auf *Ja* gesetzt ist, wird der Mindestbestellbetrag als Zwischensumme + Steuer - Rabatt berechnet.
* Wenn &quot;Steuern auf Betrag einschließen&quot;auf *NEIN* gesetzt ist, wird der Mindestbestellbetrag als Zwischensumme - Rabatt berechnet.

<u>Tatsächliche Ergebnisse</u>:

Die Bedingung der Preisregel für kostenlosen Versand kann nur auf der Zwischensumme basieren, während die Methode für kostenlosen Versand nur auf der Gesamtsumme basieren kann.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
