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

Der Patch MDVA-30837 fügt Konfigurationsoptionen für die kostenlose Versandberechnung hinzu, sodass der Benutzer den Mindestbestellbetrag so konfigurieren kann, dass er kostenlosen Versand auf Grundlage der Zwischensumme (oder Gesamtsumme) erhält. Dies ermöglicht lokale Anpassungen für Steuer- und Versandmethoden. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 ist installiert. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf Cloud-Infrastruktur 2.3.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce auf Cloud-Infrastruktur 2.3.1 - 2.3.4 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Patch MDVA-30837 fügt die Konfigurationseinstellung hinzu, um die **Mindestauftragsbetrag** Einstellung, um kostenlosen Versand auf Grundlage der Zwischensumme (oder Gesamtsumme) zu erhalten:

* **Steuern auf Betrag einschließen**: *Ja/Nein* in der Konfiguration der Versandmethode &quot;Free Shipping&quot;.
   * Wann **Steuern auf Betrag einschließen** auf *Ja*, wird der Mindestbestellbetrag als Zwischensumme + Steuern - Rabatt berechnet.
   * Wann **Steuern auf Betrag einschließen** auf *Nein*, wird der Mindestbestellbetrag als Zwischensumme - Rabatt berechnet.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **Stores** > Einstellungen > **Konfiguration** > **Vertrieb** > **Steuern** und legen Sie Folgendes fest:

   * Steuerberechnung basierend auf *Versandadresse*
   * Grenzüberschreitenden Handel aktivieren: *Nein*
   * Anzeigen von Produktionspreisen im Katalog: *Ausschließen der Steuer*
   * Versandpreise anzeigen: *Ausschließen der Steuer*
   * Anzeigepreise: *Ausschließen der Steuer*
   * Zwischensumme anzeigen: *Ausschließen der Steuer*
   * Versandbetrag anzeigen: *Ausschließen der Steuer*
   * Geschenkpreise anzeigen: *Ausschließen der Steuer*
   * Preise für gedruckte Karten anzeigen: *Ausschließen der Steuer*
   * Steuern in Bestellsumme einschließen: *Ja*
   * Vollständige Steuerzusammenfassung anzeigen: *Ja*

1. Navigieren Sie zu **Vertrieb** > **Versandeinstellungen** > **Kostenloser Versand** und **Mindestauftragsbetrag** = *30*.
1. Navigieren Sie zu **Marketing** > Promotions > **Warenkorbpreisregeln** und erstellen Sie eine neue Preisregel (detaillierte Schritte finden Sie unter [Erstellen einer Preisregel für Warenkorb](https://docs.magento.com/user-guide/marketing/price-rules-cart-create.html) in unserem Benutzerhandbuch).

   * Couponcode = *Spezifischer Gutschein*.
   * Bedingungen: Zwischensumme größer/gleich 25 USD.
   * Aktionen: Kostenloser Versand = *Für Sendungen mit übereinstimmenden Artikeln*.

1. Erstellen Sie ein Produkt mit einem Preis von 23,10 USD.
1. Fügen Sie die CA-Steuer zur Standardsteuerregel hinzu.
1. Fügen Sie dieses Produkt zum Warenkorb hinzu.
1. Erhalten Sie einen Lieferpreis - nach Steuern, die Gesamtsumme = 25,01 USD und kostenloser Versand.
1. Anwenden des Gutscheincodes - dieser ist nicht gültig, da die Zwischensumme (ohne Steuern) 23,10 USD beträgt.

<u>Erwartete Ergebnisse</u>:

Es gibt eine zusätzliche Konfigurationseinstellung - &quot;Steuern auf Betrag einschließen&quot;: *Ja*/*Nein* in der Konfiguration der Versandmethode &quot;Free Shipping&quot;:

* Wenn &quot;Steuer einschließen&quot;auf &quot;Betrag&quot;eingestellt ist auf *Ja*, wird der Mindestbestellbetrag als Zwischensumme + Steuer - Rabatt berechnet.
* Wenn &quot;Steuer einschließen&quot;auf &quot;Betrag&quot;eingestellt ist auf *Nein*, wird der Mindestbestellbetrag als Zwischensumme - Rabatt berechnet.

<u>Tatsächliche Ergebnisse</u>:

Die Bedingung der Preisregel für kostenlosen Versand kann nur auf der Zwischensumme basieren, während die Methode für kostenlosen Versand nur auf der Gesamtsumme basieren kann.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
