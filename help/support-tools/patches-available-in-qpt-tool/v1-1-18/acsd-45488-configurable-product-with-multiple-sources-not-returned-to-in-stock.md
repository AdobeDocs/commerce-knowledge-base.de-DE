---
title: "ACSD-45488: Konfigurierbares Produkt mit mehreren Quellen, die nicht automatisch auf Lager sind"
description: Der Patch ACSD-45488 behebt das Problem, dass ein konfigurierbares Produkt mit mehreren Quellen nicht automatisch auf Lager zurückgegeben wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 installiert ist. Die Patch-ID lautet ACSD-45488. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
exl-id: 83332226-b14e-4d36-bf65-170f55fff270
feature: Configuration, Orders, Products, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# ACSD-45488: Konfigurierbares Produkt mit mehreren Quellen, die nicht automatisch auf Lager sind

Der Patch ACSD-45488 behebt das Problem, dass ein konfigurierbares Produkt mit mehreren Quellen nicht automatisch auf Lager zurückgegeben wird. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 installiert ist. Die Patch-ID lautet ACSD-45488. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein konfigurierbares Produkt mit mehreren Quellen wird nicht automatisch auf Lager zurückgegeben.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine sekundäre Lagerquelle.
1. Erstellen Sie ein konfigurierbares Produkt mit zwei zugehörigen virtuellen Produkten.
1. Weisen Sie die verknüpften Produkte der Standardlagerquelle zu und setzen Sie die Menge auf 1.
1. Überprüfen Sie die `stock_status` von `cataloginventory_stock_status`.
1. Setzen Sie beide verknüpften Produkte auf *nicht vorrätig*.
1. Überprüfen Sie die `stock_status` von `cataloginventory_stock_status`.
1. Setzen Sie beide verknüpften Produkte auf *auf Lager*.
1. Überprüfen Sie die `stock_status` von `cataloginventory_stock_status`.

<u>Erwartete Ergebnisse</u>:

Der Lagerstatus des konfigurierbaren Produkts wird auf *auf Lager* wenn die verknüpften Produkte auf Lager eingestellt sind.

<u>Tatsächliche Ergebnisse</u>:

Der Lagerstatus des konfigurierbaren Produkts wird nicht aktualisiert auf *auf Lager* wenn die verknüpften Produkte auf Lager eingestellt sind.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
