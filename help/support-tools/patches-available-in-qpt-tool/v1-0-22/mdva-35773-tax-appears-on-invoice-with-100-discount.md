---
title: "MDVA-35773: Die Steuer wird auf der Rechnung mit 100% Rabatt angezeigt."
description: Der Patch MDVA-35773 behebt das Problem, bei dem die Gesamtsumme nicht als Null auf der Rechnung für Bestellungen mit 100% Rabatt angezeigt wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 installiert ist. Die Patch-ID lautet MDVA-35773. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.
exl-id: 895cb7d3-be9f-4864-9658-87ee0471f556
feature: Invoices, Marketing Tools, Orders, Personalization, Taxes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-35773: Steuern werden auf Rechnung mit 100% Rabatt angezeigt

Der Patch MDVA-35773 behebt das Problem, bei dem die Gesamtsumme nicht als Null auf der Rechnung für Bestellungen mit 100% Rabatt angezeigt wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 installiert ist. Die Patch-ID lautet MDVA-35773. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.3.6

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce lokal und Adobe Commerce auf Cloud-Infrastruktur 2.3.6-2.3.7 und 2.4.1-2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **Stores** > **Einstellungen** > **Konfiguration** > **Verkauf** > **Steuern**.
1. Legen Sie **Katalogpreise** und **Rabatt auf Preise** auf *Einschließlich Steuern* fest.
1. Navigieren Sie zu **Geschäfte** > **Steuerregeln** > **Neue Steuerregel hinzufügen**.
1. Erstellen Sie eine Steuerregel (Beispiel: alle USA mit 10% Steuersatz) und wenden Sie sie an.
1. Navigieren Sie zu **Marketing** > **Warenkorbpreisregeln** und **Neue Regel hinzufügen**.
1. Erstellen Sie eine Regel mit einem **100 % Rabatt für alle Benutzer**.
1. Bestellen Sie in der Storefront:

   * Wählen Sie **Free Shipping**.
   * Wenden Sie **Couponcode** an.

1. Navigieren Sie zu **Verkauf** > **Bestellungen** und öffnen Sie Ihre Bestellung.
1. Erstellen Sie eine Rechnung für die Bestellung und öffnen Sie sie.

<u>Erwartete Ergebnisse</u>:

Die Rechnungssumme = *$0.00*.

<u>Tatsächliche Ergebnisse</u>:

Die Rechnungssumme = *Steuerbetrag* wird erstellt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
