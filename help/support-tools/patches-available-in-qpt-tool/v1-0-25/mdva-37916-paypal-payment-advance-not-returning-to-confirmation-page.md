---
title: "MDVA-37916: PayPal Payments Advanced not return to validation page"
description: Der Qualitätspatch MDVA-37916 für Adobe Commerce behebt das Problem, dass PayPal Payments Advanced nach der Zahlung nicht auf die Bestätigungsseite zurückkehrt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 installiert ist. Die Patch-ID lautet MDVA-37916. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: 18d7bb1c-d73a-43f6-90a8-650290dfd114
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# MDVA-37916: PayPal Payments Advanced not return to validation page

Der Qualitätspatch MDVA-37916 für Adobe Commerce behebt das Problem, dass PayPal Payments Advanced nach der Zahlung nicht auf die Bestätigungsseite zurückkehrt. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 ist installiert. Die Patch-ID lautet MDVA-37916. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
Adobe Commerce auf Cloud-Infrastruktur 2.3.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**
Adobe Commerce On-Premise und Adobe Commerce über Cloud-Infrastruktur 2.3.6-2.4.2-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Kunde wird nach der Zahlung nicht auf die Zahlungsbestätigungsseite geleitet, wenn er die Methode PayPal Payments Advanced verwendet.

<u>Zu reproduzierende Schritte</u>: [Screencast](https://assets.adobe.com/public/025d479b-5796-4772-6f3d-adc86306a799)

1. Fügen Sie das Produkt zum Warenkorb hinzu und navigieren Sie zum Zahlungsschritt der Checkout-Seite.
1. Auswählen **Kreditkarte (Zahlungsfluss erweitert)** Zahlungsoption.
1. Klicks **Weiter** , um den iframe mit dem Zahlungsformular anzuzeigen.
1. Füllen Sie das Zahlungsformular mit Sandbox-Kreditkartendetails aus.
   * Kartennummer: 444 3333 222 1111 oder 4111 111 111 111 1111
   * Ablaufdatum: 23.12.23
   * CSC: 123
1. Klicks **Jetzt bezahlen**.

<u>Erwartete Ergebnisse</u>:

Nachdem die Zahlung verarbeitet wurde und die Zahlung erfolgreich war, werden Sie auf die Bestellbestätigungsseite weitergeleitet.

<u>Tatsächliche Ergebnisse</u>:

* Sie werden NICHT zur Bestellbestätigungsseite weitergeleitet.
* Die Bestellung wurde jedoch in Adobe Commerce erstellt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html)

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster in unserer Wissensdatenbank finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) in unserer Support-Wissensdatenbank.
