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

Der Patch MDVA-42969 behebt das Problem, dass die zugehörige Produktregel nur funktioniert, wenn das Kundensegment auf &quot;Alle&quot;gesetzt ist. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-42969. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die zugehörige Produktregel funktioniert nur, wenn das Kundensegment auf &quot;Alle&quot;festgelegt ist.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **Stores** > **Konfiguration** > **Katalog** > **Regelbasierte Produktbeziehungen** und **Verwandte Produkte anzeigen** = **Nur regelbasiert**.
1. Navigieren Sie zu **Kunden** > **Segmente** und erstellen Sie ein neues Segment: **Anwenden auf** = **Besucher und registrierte Kunden**.
1. Navigieren Sie zu **Marketing** > **Verwandte Produktregeln** und erstellen Sie eine neue Regel.

   ```code block
   Apply To = Related Products
   Customer Segments = All
   Products to Match = SKU = <select a SKU>
   Products to Display = SKU +is one of+ Constant Value (specify 1-3 products)
   ```

1. Öffnen Sie das entsprechende Produkt auf der Storefront und überprüfen Sie, ob die anzuzeigenden Produkte angezeigt werden.
1. Ändern Sie die in Schritt 3 erstellte Regel und legen Sie **Kundensegmente** = **spezifisch** > **Segment** aus Schritt 2.
1. Öffnen Sie das entsprechende Produkt auf der Storefront.

<u>Erwartete Ergebnisse</u>:

Regelbasierte verwandte Produkte werden auf der Storefront für Besucher des Produkts angezeigt, da das Kundensegment mit der folgenden Konfiguration erstellt wird:

**Anwenden auf** = **Besucher und registrierte Kunden**

<u>Tatsächliche Ergebnisse</u>:

Es werden keine verwandten Produkte angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
