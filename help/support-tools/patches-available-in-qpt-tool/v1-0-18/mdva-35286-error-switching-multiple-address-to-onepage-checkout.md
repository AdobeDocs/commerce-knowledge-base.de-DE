---
title: "MDVA-35286: error switch multiple Address to Onepage checkout"
description: Der Patch MDVA-35286 behebt das Problem, bei dem ein Fehler auftritt, wenn ein Kunde Bundle-Produkte im Warenkorb hat und von "Multiple Address Checkout"zum "Onepage Checkout"wechselt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 installiert ist. Die Patch-ID lautet MDVA-35286. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
exl-id: 40c98735-6054-4b25-9882-e274424b203f
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-35286: Fehler beim Wechseln von Multiple Address zu Onepage-Checkout

Der Patch MDVA-35286 behebt das Problem, bei dem ein Fehler auftritt, wenn ein Kunde Bundle-Produkte im Warenkorb hat und von &quot;Multiple Address Checkout&quot;zum &quot;Onepage Checkout&quot;wechselt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 installiert ist. Die Patch-ID lautet MDVA-35286. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0-2.4.1-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein Fehler wird angezeigt, wenn sich ein Paket-Produkt im Warenkorb befindet und der Benutzer versucht, Onepage Checkout zu verwenden, nachdem er das Multi-Shipping Checkout abgebrochen hat.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Kundenkonto an und fügen Sie dem Warenkorb mehr als ein Bundle-Produkt hinzu.
1. Klicken Sie auf den Link, um den Warenkorb anzuzeigen und zu bearbeiten.
1. Klicken Sie auf den Link **Mit mehreren Adressen auschecken** .
1. Wählen Sie verschiedene Adressen für Produkte aus, die zum Warenkorb hinzugefügt werden.
1. Klicken Sie auf **Zurück zum Warenkorb**.
1. Klicken Sie im Warenkorb auf **Fahren Sie mit dem Checkout fort**.

<u>Erwartete Ergebnisse</u>:

Sie werden zur Seite &quot;Auschecken&quot;weitergeleitet.

<u>Tatsächliche Ergebnisse</u>:

Die Fehlermeldung wird angezeigt: *Bei der Verarbeitung Ihrer Anfrage ist ein Fehler aufgetreten*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
