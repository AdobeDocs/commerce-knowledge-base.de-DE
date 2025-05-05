---
title: 'ACSD-45488: Konfigurierbares Produkt mit mehreren Quellen, das nicht automatisch auf Lager zurückgegeben wird'
description: Der Patch ACSD-45488 löst das Problem, dass ein konfigurierbares Produkt mit mehreren Quellen nicht automatisch auf Lager zurückgegeben wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 installiert ist. Die Patch-ID ist ACSD-45488. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.
exl-id: 83332226-b14e-4d36-bf65-170f55fff270
feature: Configuration, Orders, Products, Returns
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# ACSD-45488: Konfigurierbares Produkt mit mehreren Quellen, das nicht automatisch auf Lager zurückgegeben wird

Der Patch ACSD-45488 löst das Problem, dass ein konfigurierbares Produkt mit mehreren Quellen nicht automatisch auf Lager zurückgegeben wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 installiert ist. Die Patch-ID ist ACSD-45488. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein konfigurierbares Produkt mit mehreren Quellen wird nicht automatisch auf Lager zurückgegeben.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine sekundäre Lagerquelle.
1. Erstellen Sie ein konfigurierbares Produkt mit zwei zugehörigen virtuellen Produkten.
1. Weisen Sie die zugehörigen Produkte der standardmäßigen Lagerquelle zu und legen Sie die Menge auf 1 fest.
1. Überprüfen Sie die `stock_status` aus `cataloginventory_stock_status`.
1. Legen Sie fest, dass die beiden zugehörigen Produkte *nicht vorrätig* sind.
1. Überprüfen Sie die `stock_status` aus `cataloginventory_stock_status`.
1. Legen Sie beide zugehörigen Produkte als &quot;*&quot;*.
1. Überprüfen Sie die `stock_status` aus `cataloginventory_stock_status`.

<u>Erwartete Ergebnisse</u>:

Der Lagerstatus des konfigurierbaren Produkts wird auf &quot;*&quot; aktualisiert* wenn die zugehörigen Produkte als „auf Lager“ festgelegt sind.

<u>Tatsächliche Ergebnisse</u>:

Der Lagerstatus des konfigurierbaren Produkts wird nicht auf &quot;*&quot; aktualisiert* wenn die zugehörigen Produkte als „auf Lager“ festgelegt sind.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
