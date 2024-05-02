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

Der Patch MDVA-31282 behebt das Problem, wenn auf Paypal PayFlow Pro in Adobe Commerce doppelte Berechtigungen erteilt werden. Die doppelten Genehmigungen haben auch zur Folge, dass die Betrugsfilter von PayFlow Pro umgangen und die Transaktionsgebühren verdoppelt werden. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 ist installiert.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.2 - 2.3.3 und 2.3.5 - 2.3.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

In PayPal PayFlow Pro in Adobe Commerce gibt es doppelte Berechtigungen, die dazu führen, dass die Betrugsfilter von PayFlow Pro umgangen und die Transaktionsgebühren verdoppelt werden.

<u>Voraussetzungen</u>:

PayPal PayFlow Pro Zahlungsmethode konfigurieren.

<u>Zu reproduzierende Schritte</u>:

1. Besuchen Sie das Frontend als Gastkunden.
1. Hinzufügen von Produkten zu **Warenkorb** von Produktseiten.
1. Fahren Sie mit **Checkout**.
1. Angeben **Versandadresse** als Adresse in Land \#1 (Beispiel: Adresse des Vereinigten Königreichs) und wählen Sie eine Versandmethode aus.
1. Auswählen **PayPal PayFlow Pro** als Zahlungsmethode. Geben Sie die **Rechnungsadresse** als Adresse in Land \#2 (Beispiel: US-Adresse).
1. Geben Sie Kreditkartendaten ein und geben Sie die Bestellung auf.
1. Navigieren Sie zu **Vertrieb** > **Bestellungen** in Admin und beobachten die erstellte Reihenfolge.

<u>Erwartete Ergebnisse</u>:

* Der Baustein Zahlungsinformationen wird angezeigt: *&quot;Ausgelöste Betrugsfilter: RESPMSG: Wird von Fraud Service überprüft*. *Die Bestellung weist den Status &quot;Verdächtiger Betrug&quot;auf.*.
* Paypal PayFlow Pro zeigt eine einzige Autorisierungsaktion wie erwartet an.

<u>Tatsächliche Ergebnisse</u>:

* Der Baustein Zahlungsinformationen wird angezeigt: *&quot;Ausgelöste Betrugsfilter: RESPMSG: Wird von Fraud Service überprüft*. *Die Bestellung befindet sich im Verarbeitungsstatus&quot;*.
* Paypal PayFlow Pro zeigt Transaktionen mit doppelter Autorisierung an.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
