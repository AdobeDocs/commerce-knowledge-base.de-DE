---
title: 'MDVA-41597: Fehler beim Hinzufügen von mehr als einem konfigurierbaren Produkt zum Warenkorb'
description: Der Patch MDVA-41597 behebt das Problem, dass Benutzende einen Fehler erhalten, wenn sie mit GraphQL mehr als ein konfigurierbares Produkt zum Warenkorb hinzufügen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-41597. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
exl-id: 777e0f9c-80e3-4cfb-9328-c20eb038f74a
feature: Configuration, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# MDVA-41597: Fehler beim Hinzufügen von mehr als einem konfigurierbaren Produkt zum Warenkorb

Der Patch MDVA-41597 behebt das Problem, dass Benutzende einen Fehler erhalten, wenn sie mit GraphQL mehr als ein konfigurierbares Produkt zum Warenkorb hinzufügen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-41597. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzende erhalten eine Fehlermeldung, wenn sie mit GraphQL mehr als ein konfigurierbares Produkt zum Warenkorb hinzufügen.

<u>Schritte zur Reproduktion</u>:

Fügen Sie mehrere konfigurierbare Produkte mit GraphQL-Mutation zum Warenkorb hinzu: `addConfigurableProductsToCart`.

<u>Erwartete Ergebnisse</u>:

Alle konfigurierbaren Produkte werden zum Warenkorb hinzugefügt.

<u>Tatsächliche Ergebnisse</u>:

Nur das erste Produkt wird zum Warenkorb hinzugefügt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
