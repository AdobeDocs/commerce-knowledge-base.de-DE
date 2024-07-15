---
title: "MDVA-31224 Patch: Produktpreis für Neuindizierung dauert zu lange"
description: Der Patch MDVA-31224 löst das Problem, wenn die Neuindizierung des Produktpreises zu lange dauert, um abgeschlossen zu werden oder nie abgeschlossen zu werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.7 installiert ist.
exl-id: 17f83fbf-9a43-4a65-b560-5f729b037c17
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# MDVA-31224 Patch: Der Produktpreis für die Neuindizierung dauert zu lange

Der Patch MDVA-31224 löst das Problem, wenn die Neuindizierung des Produktpreises zu lange dauert, um abgeschlossen zu werden oder nie abgeschlossen zu werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.7 installiert ist.

## Betroffene Produkte und Versionen

* Der Patch wurde für Adobe Commerce in der Cloud-Infrastruktur 2.3.3 entwickelt.
* Der Patch ist auch mit Adobe Commerce On-Premise und Adobe Commerce in der Cloud-Infrastruktur 2.3.3 - 2.3.4-p2 kompatibel.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Neuindizierung des Produktpreises dauert zu lange, um abgeschlossen zu werden oder nie abgeschlossen zu werden.

<u>Zu reproduzierende Schritte:</u>

1. Erstellen Sie 6000 gebündelte Produkte mit 15 Optionen.
1. Erstellen Sie ein gebündeltes Produkt mit 30 Optionen.
1. Führen Sie die Preisneuindizierung über die CLI aus:     `bin/magento indexer:reindex catalog_product_price`

<u>Erwartete Ergebnisse:</u>

Die Neuindizierung des Produktpreises dauert 1,5 Stunden oder länger.

<u>Tatsächliche Ergebnisse:</u>

Die Neuindizierung des Produktpreises dauert eine kurze Zeit (eine Minute oder zwei).

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
