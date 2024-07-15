---
title: "MDVA-36833: defekte Paginierung auf Suchergebnisseite"
description: Der Patch MDVA-36833 behebt das Problem, dass die Paginierung unterbrochen wird, wenn der freigegebene Katalog aktiviert ist und einige Produkte aus dem freigegebenen Katalog ausgeschlossen wurden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 installiert ist. Die Patch-ID lautet MDVA-36833. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.
exl-id: 7105c4ed-48d9-4d4c-bf12-5914bbad62da
feature: Catalog Management, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-36833: Seitenumbruch auf Suchergebnisseite

Der Patch MDVA-36833 behebt das Problem, dass die Paginierung unterbrochen wird, wenn der freigegebene Katalog aktiviert ist und einige Produkte aus dem freigegebenen Katalog ausgeschlossen wurden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 installiert ist. Die Patch-ID lautet MDVA-36833. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Ausschließen einiger Produkte aus einem freigegebenen Katalog führt zu einer fehlerhaften Paginierung für Suchergebnisse.

<u>Zu reproduzierende Schritte:</u>

1. Aktivieren Sie den freigegebenen Katalog.
1. Navigieren Sie zu **Katalog** > **Gemeinsame Kataloge** und richten Sie den standardmäßigen freigegebenen Katalog ein, indem Sie ihm alle Produkte zuweisen.
1. Laden Sie die Storefront und suchen Sie nach &quot;Jacke&quot;.
1. Beachten Sie die auf der ersten Seite aufgelisteten Produkte. Es sollte zwölf Produkte geben.
1. Beachten Sie 11 SKUs von der ersten Seite. Gehen Sie zum Backend und laden Sie den freigegebenen Standardkatalog.
1. Heben Sie die Zuweisung zuvor angegebener SKUs aus dem freigegebenen Standardkatalog auf.
1. Gehen Sie zur Storefront und suchen Sie nach &quot;Jacke&quot;.
1. Überprüfen Sie die erste Seite der Suchergebnisse.

<u>Tatsächliches Ergebnis:</u>

Die erste Seite enthält ein Produkt und der Rest der Produkte ist auf der zweiten Seite verfügbar.

<u>Erwartetes Ergebnis:</u>

Die erste Seite sollte 12 Produkte enthalten.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.


## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
