---
title: 'MDVA-43605: Bestelldaten geben bei Verwendung der REST-API negative Werte für Zeilensummen zurück'
description: Der Patch MDVA-43605 behebt das Problem, dass die Bestelldaten bei Verwendung der REST-API negative Werte für Zeilensummen zurückgeben. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43605. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: 8a679e85-1681-42c3-b072-18797198bdc4
feature: REST, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# MDVA-43605: Bestelldaten geben bei Verwendung der REST-API negative Werte für Zeilensummen zurück

Der Patch MDVA-43605 behebt das Problem, dass die Bestelldaten bei Verwendung der REST-API negative Werte für Zeilensummen zurückgeben. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43605. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Bestelldaten geben bei Verwendung der REST-API negative Werte für Zeilensummen zurück.

<u>Schritte zur Reproduktion</u>:

1. Kostenlosen Versand aktivieren.
1. Navigieren Sie **Konfiguration** > **Katalog** > **Preis** > und legen Sie Katalogpreis Umfang = Website fest.
1. Navigieren Sie zu **Konfiguration** > **Verkauf** > **Steuer** und aktualisieren Sie:
   * Steuerklasse für den Versand = steuerpflichtige Waren
   * Berechnungsparameter:
      * Katalogpreis = inkl. MwSt
      * Versandpreis = inkl. Preis
      * Preisnachlass = inkl. Steuer
   * Einstellungen für die Preisanzeige: Einschließlich Steuer (alle Felder)
   * Anzeigeeinstellungen für den Warenkorb: Einschließlich Steuer (alle Felder)
   * Bestellungen, Rechnungen, Gutschriften:
      * Versandbetrag anzeigen = einschließlich MwSt
1. Steuersatz für USA erstellen (Bundesland = &#39;*&#39;), Steuersatz Prozent = 24,00
1. Erstellen Sie eine Steuerregel mit dem obigen Steuersatz.
1. Erstellen Sie eine Warenkorb-Preisregel mit einem bestimmten Coupon und Rabatt = 50 $ des Festbetrags für den gesamten Warenkorb.
1. Erstellen Sie vier Produkte zu folgenden Preisen: $8.90, $5.90, $6.90 und $5.95.
1. Erstellen Sie eine Admin-Bestellung mit vier dieser Produkte unter Verwendung des im vorherigen Schritt erstellten Couponcodes. Verwenden Sie den kostenlosen Versand.
1. Die Zahlung sollte nicht erforderlich sein, da der Couponcode die Gesamtsumme des Warenkorbs abdeckt.
1. Rufen Sie die gerade über den REST-API-Endpunkt erstellte Reihenfolge ab:

   ```json
   GET rest/V1/orders/1
   ```

<u>Erwartete Ergebnisse</u>:

Die Werte von `base_row_total` und `base_row_total_incl_tax` in der Antwort sind null.

<u>Tatsächliche Ergebnisse</u>:

Die Felder `base_row_total` und `base_row_total_incl_tax` in der Antwort haben negative Werte.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in unserer Entwicklerdokumentation.
