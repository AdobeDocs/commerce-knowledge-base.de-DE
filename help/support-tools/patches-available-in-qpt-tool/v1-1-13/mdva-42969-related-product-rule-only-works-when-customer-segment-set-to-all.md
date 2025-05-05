---
title: 'MDVA-42969: Die Regel für verwandte Produkte funktioniert nur, wenn das Kundensegment auf „Alle“ festgelegt ist'
description: Mit dem Patch MDVA-42969 wird das Problem behoben, dass die zugehörige Produktregel nur funktioniert, wenn das Kundensegment auf „Alle“ festgelegt ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-42969. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: 2877ba7a-2681-4de2-9c37-228de232424f
feature: Customer Service, Marketing Tools, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-42969: Die Regel für verwandte Produkte funktioniert nur, wenn das Kundensegment auf „Alle“ festgelegt ist

Mit dem Patch MDVA-42969 wird das Problem behoben, dass die zugehörige Produktregel nur funktioniert, wenn das Kundensegment auf „Alle“ festgelegt ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-42969. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die zugehörige Produktregel funktioniert nur, wenn das Kundensegment auf „Alle“ festgelegt ist.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie **Stores** > **Konfiguration** > **Katalog** > **Regelbasierte Produktbeziehungen** und **Zugehörige Produkte anzeigen** = **Nur regelbasierte**.
1. Gehen Sie zu **Kunden** > **Segmente** und erstellen Sie ein neues Segment: **Anwenden auf** = **Besucher und registrierte Kunden**.
1. Gehen Sie zu **Marketing** > **Zugehörige Produktregeln** und erstellen Sie eine neue Regel.

   ```code block
   Apply To = Related Products
   Customer Segments = All
   Products to Match = SKU = <select a SKU>
   Products to Display = SKU +is one of+ Constant Value (specify 1-3 products)
   ```

1. Öffnen Sie das entsprechende Produkt in der Storefront und überprüfen Sie, ob die anzuzeigenden Produkte angezeigt werden.
1. Ändern Sie die in Schritt 3 erstellte Regel und setzen Sie **Kundensegmente** = **spezifisch** > **Segment** aus Schritt 2.
1. Öffnen Sie das entsprechende Produkt in der Storefront.

<u>Erwartete Ergebnisse</u>:

Regelbasierte verwandte Produkte werden für Besucher auf dem Produkt in der Storefront angezeigt, da das Kundensegment mit der folgenden Konfiguration erstellt wird:

**Apply To** = **Besucher und registrierte Kunden**

<u>Tatsächliche Ergebnisse</u>:

Es werden keine verwandten Produkte angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
