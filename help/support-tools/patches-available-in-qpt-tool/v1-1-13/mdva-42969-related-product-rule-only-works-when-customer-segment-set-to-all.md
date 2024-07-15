---
title: '"MDVA-42969: Zugehörige Produktregel funktioniert nur, wenn das Kundensegment auf "Alle"gesetzt ist.'
description: Der Patch MDVA-42969 behebt das Problem, dass die zugehörige Produktregel nur funktioniert, wenn das Kundensegment auf "Alle"gesetzt ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-42969. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: 2877ba7a-2681-4de2-9c37-228de232424f
feature: Customer Service, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-42969: Zugehörige Produktregel funktioniert nur, wenn das Kundensegment auf alle eingestellt ist

Der Patch MDVA-42969 behebt das Problem, dass die zugehörige Produktregel nur funktioniert, wenn das Kundensegment auf &quot;Alle&quot;gesetzt ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-42969. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die zugehörige Produktregel funktioniert nur, wenn das Kundensegment auf &quot;Alle&quot;festgelegt ist.

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu **Stores** > **Konfiguration** > **Katalog** > **Regelbasierte Produktbeziehungen** und legen Sie **Zugehörige Produkte anzeigen** = **Nur regelbasiert** fest.
1. Gehen Sie zu **Kunden** > **Segmente** und erstellen Sie ein neues Segment: **Anwenden auf** = **Besucher und registrierte Kunden**.
1. Gehen Sie zu **Marketing** > **Zugehörige Produktregeln** und erstellen Sie eine neue Regel.

   ```code block
   Apply To = Related Products
   Customer Segments = All
   Products to Match = SKU = <select a SKU>
   Products to Display = SKU +is one of+ Constant Value (specify 1-3 products)
   ```

1. Öffnen Sie das entsprechende Produkt auf der Storefront und überprüfen Sie, ob die anzuzeigenden Produkte angezeigt werden.
1. Ändern Sie die in Schritt 3 erstellte Regel und legen Sie **Kundensegmente** = **Spezifische** > **Segment** in Schritt 2 fest.
1. Öffnen Sie das entsprechende Produkt auf der Storefront.

<u>Erwartete Ergebnisse</u>:

Regelbasierte verwandte Produkte werden auf der Storefront für Besucher des Produkts angezeigt, da das Kundensegment mit der folgenden Konfiguration erstellt wird:

**Anwenden auf** = **Besucher und registrierte Kunden**

<u>Tatsächliche Ergebnisse</u>:

Es werden keine verwandten Produkte angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
