---
title: MDVA-28357 SKU-Suche auf der Seite "Erweiterte Suche"funktioniert nicht
description: MDVA-28357 behebt das Problem, dass die Suche nach einer Produkt-SKU auf der Seite "Erweiterte Suche"nicht dazu führt, dass das relevante Produkt in den Suchergebnissen angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce Version 2.4.1 behoben ist.
exl-id: a89409b0-3155-4fac-9842-0d129dacd6e1
feature: Search
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-28357 SKU-Suche auf der Seite &quot;Erweiterte Suche&quot;funktioniert nicht

MDVA-28357 behebt das Problem, dass die Suche nach einer Produkt-SKU auf der Seite &quot;Erweiterte Suche&quot;nicht dazu führt, dass das relevante Produkt in den Suchergebnissen angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce Version 2.4.1 behoben ist.

## Betroffene Produkte und Versionen

* Dieser Patch wurde für Adobe Commerce On-Premise 2.3.4-p2 entwickelt.
* Der Patch ist auch mit Adobe Commerce On-Premise und Adobe Commerce in der Cloud-Infrastruktur 2.3.0 bis 2.3.5-p2 und 2.4.0 bis 2.4.0-p1 kompatibel.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Bei der erweiterten Suche fragt die Suche mithilfe einer SKU das SKU-Feld mithilfe eines Platzhalters ab. Ein Platzhalter kann jedoch nur mit `sku.keyword` verwendet werden, sodass nicht das erwartete Produkt zurückgegeben wird.

<u>Zu reproduzierende Schritte</u>

1. Navigieren Sie zur Seite Erweiterte Suche .
1. Suchen Sie nach einer SKU-Nummer.

<u>Tatsächliches Ergebnis</u>

Fehlermeldung wird angezeigt: *Wir können keine Elemente finden, die diesen Suchkriterien entsprechen. Ändern Sie Ihre Suche*.

<u>Erwartetes Ergebnis</u>

Ein Produktelement wird mit einer Meldung angezeigt: *1 Element wurde mithilfe der folgenden Suchkriterien gefunden* *SKU: XX-XXXX*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Wenden Sie Patches mithilfe des Qualitätssicherungswerkzeugs für Qualitätsmuster an](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitätspatches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Überprüfen Sie mithilfe des Qualitätssicherungswerkzeugs](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md), ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
