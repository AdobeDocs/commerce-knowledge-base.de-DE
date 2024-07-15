---
title: "MDVA-31282: double authorization on Paypal PayFlow Pro"
description: Der Patch MDVA-31282 behebt das Problem, wenn auf Paypal PayFlow Pro in Adobe Commerce doppelte Berechtigungen erteilt werden. Die doppelten Genehmigungen haben auch zur Folge, dass die Betrugsfilter von PayFlow Pro umgangen und die Transaktionsgebühren verdoppelt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 installiert ist.
exl-id: f239012e-e1bd-474b-aad2-7218ec3a3d1b
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-31282: Doppelautorisierung für Paypal PayFlow Pro

Der Patch MDVA-31282 behebt das Problem, wenn auf Paypal PayFlow Pro in Adobe Commerce doppelte Berechtigungen erteilt werden. Die doppelten Genehmigungen haben auch zur Folge, dass die Betrugsfilter von PayFlow Pro umgangen und die Transaktionsgebühren verdoppelt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 installiert ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.2 - 2.3.3 und 2.3.5 - 2.3.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

In PayPal PayFlow Pro in Adobe Commerce gibt es doppelte Berechtigungen, die dazu führen, dass die Betrugsfilter von PayFlow Pro umgangen und die Transaktionsgebühren verdoppelt werden.

<u>Voraussetzungen</u>:

PayPal PayFlow Pro Zahlungsmethode konfigurieren.

<u>Zu reproduzierende Schritte</u>:

1. Besuchen Sie das Frontend als Gastkunden.
1. Fügen Sie Produkte zu **Warenkorb** von Produktseiten hinzu.
1. Fahren Sie mit **Checkout** fort.
1. Geben Sie **Versandadresse** als Adresse in Land \#1 ein (Beispiel: UK-Adresse) und wählen Sie eine Versandmethode aus.
1. Wählen Sie **PayPal PayFlow Pro** als Zahlungsmethode aus. Geben Sie die **Rechnungsadresse** als Adresse in Land \#2 (Beispiel: US-Adresse) an.
1. Geben Sie Kreditkartendaten ein und geben Sie die Bestellung auf.
1. Navigieren Sie in Admin zu **Verkauf** > **Bestellungen** und beobachten Sie die erstellte Bestellung.

<u>Erwartete Ergebnisse</u>:

* Der Baustein Zahlungsinformationen zeigt: *&quot;Ausgelöste Betrugsfilter: RESPMSG: Wird von Fraud Service überprüft*. *Die Bestellung befindet sich im Status &quot;Verdächtiger Betrug&quot;*.
* Paypal PayFlow Pro zeigt eine einzige Autorisierungsaktion wie erwartet an.

<u>Tatsächliche Ergebnisse</u>:

* Der Baustein Zahlungsinformationen zeigt: *&quot;Ausgelöste Betrugsfilter: RESPMSG: Wird von Fraud Service überprüft*. *Die Bestellung befindet sich im Verarbeitungsstatus&quot;*.
* Paypal PayFlow Pro zeigt Transaktionen mit doppelter Autorisierung an.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
