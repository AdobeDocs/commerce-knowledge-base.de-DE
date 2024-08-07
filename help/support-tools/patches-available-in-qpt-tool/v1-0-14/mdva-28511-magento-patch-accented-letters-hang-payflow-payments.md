---
title: "MDVA-28511: Akzentbuchstaben hängen Zahlungen für Zahlungsströme"
description: Der Patch MDVA-28511 behebt das Problem, wenn Zahlungen über **Payflow Pro** nicht für Kundennamen mit Akzentzeichen abgeschlossen werden.
exl-id: ecc827e3-2a1c-4f32-a0e2-9c5792483e7d
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MDVA-28511: Akzentuierte Briefe hängen Zahlungen für Zahlungsströme

Der Patch MDVA-28511 behebt das Problem, wenn Zahlungen über **Payflow Pro** nicht für Kundennamen mit Akzentzeichen abgeschlossen werden.

Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.3.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce für die Cloud-Infrastruktur 2.3.5-p1

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce für Cloud-Infrastruktur und Adobe Commerce On-Premise 2.3.5 - 2.3.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Voraussetzung</u>:

Aktivieren Sie die Kreditkartenzahlmethode **Payflow Pro**.

<u>Zu reproduzierende Schritte</u>:

1. Fügen Sie ein Produkt zum Warenkorb hinzu und fahren Sie mit der Checkout-Seite fort.
1. Festlegen eines Kundennamens mit Akzenten. (Beispiel: **Ãtienne Ãillin**)
1. Fahren Sie mit den Zahlungsschritten fort.
1. Wählen Sie **Payflow Pro** als **Kreditkarte** aus und geben Sie die Kreditkartendetails ein.
1. Klicken Sie auf die Schaltfläche **Bestellung platzieren** .

<u>Erwartete Ergebnisse</u>:

Die Bestellung wird wie erwartet ohne Ausgabe abgeschlossen.

<u>Tatsächliche Ergebnisse</u>:

Die Reihenfolge wird nicht abgeschlossen und die Protokolle zeigen einen ähnlichen Fehler wie im folgenden Beispiel:

```php
[2020-06-12 07:50:23] report.CRITICAL: String to be escaped was not valid UTF-8 or could not be converted: �?tienne �?illini [] []
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) verfügbare Patches.
