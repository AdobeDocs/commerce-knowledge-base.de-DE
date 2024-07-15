---
title: "MDVA-37182: Inkonsistente Suchergebnisse in Elasticsearch 6 und 7"
description: Der Patch MDVA-37182 behebt das Problem mit inkonsistentem Suchverhalten in den Versionen 6 und 7 von Elasticsearch. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 installiert ist. Die Patch-ID lautet MDVA-37182. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.
exl-id: 6c4e2d2f-cced-487d-b253-fd0c80bc6067
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-37182: Inkonsistente Suchergebnisse in Elasticsearch 6 und 7

Der Patch MDVA-37182 behebt das Problem mit inkonsistentem Suchverhalten in den Versionen 6 und 7 von Elasticsearch. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 installiert ist. Die Patch-ID lautet MDVA-37182. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce in der Cloud-Infrastruktur 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce On-Premise und Adobe Commerce in der Cloud-Infrastruktur 2.4.1-2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Inkonsistentes Suchverhalten.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie Produkte mit den folgenden Details:
   * Namen: &quot;5127AC&quot;, &quot;5127SS&quot;, &quot;5127AB&quot;
   * SKUs: &quot;product1&quot;, &quot;product2&quot;, &quot;product3&quot;
1. Setzen Sie die Suchmaschine auf Elasticsearch 6 (ES6).
1. Führen Sie die vollständige Neuindizierung aus.
1. Suchen Sie in der Storefront nach &quot;5127s&quot;.
1. Setzen Sie die Suchmaschine auf Elasticsearch 7 (ES7).
1. Führen Sie die vollständige Neuindizierung aus.
1. Suchen Sie in der Storefront nach &quot;5127s&quot;.

<u>Tatsächliches Ergebnis:</u>:

ES6: Die Suche gibt keine Ergebnisse zurück.ES7: Die Suche gibt drei Produkte zurück.

<u>Erwartetes Ergebnis:</u>:

Die Suche gibt für beide Versionen ein Produkt zurück.

## Wenden Sie den Patch an

Verwenden Sie je nach Adobe Commerce-Produkt die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
