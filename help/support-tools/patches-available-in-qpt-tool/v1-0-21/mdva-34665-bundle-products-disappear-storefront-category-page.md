---
title: "MDVA-34665: Bundle-Produkte verschwinden Storefront-Kategorieseite"
description: Der Patch MDVA-34665 behebt das Problem mit fehlenden gebündelten Produkten auf Kategorieseiten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 installiert ist. Die Patch-ID lautet MDVA-34665. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.
exl-id: 2b393f91-de0d-4c54-89db-5e2af13f93a6
feature: Categories, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---

# MDVA-34665: Bundle-Produkte verschwinden Storefront-Kategorieseite

Der Patch MDVA-34665 behebt das Problem mit fehlenden gebündelten Produkten auf Kategorieseiten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 installiert ist. Die Patch-ID lautet MDVA-34665. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce vor Ort und Adobe Commerce über Cloud-Infrastruktur 2.3.4-2.3.4-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

**1:**

<u>Voraussetzungen</u>:

1. Erstellen Sie 15.000 gebündelte Produkte mit einem einfachen Produkt als Bundle-Option. Verwenden Sie nicht dasselbe einfache Produkt mit mehreren gebündelten Produkten.
1. Einfache Produkte sollten auf *Nicht einzeln sichtbar* gesetzt werden.

<u>Zu reproduzierende Schritte</u>:

1. Weisen Sie 15.000 gebündelte Produkte in zwei Kategorien zu, jeweils 7.500.
1. Wählen Sie alle einfachen Produkte (15.000) aus und aktualisieren Sie den Bestand mithilfe von Aktualisierungen des Massenattributs des Produkts. Unser Ziel ist es, viele IDs in der Suchtabelle zu haben (cl-Tabellen sind die Tabellen, die vom Indexer verwendet werden, um zu erfahren, welche Datensätze aktualisiert werden müssen.)
1. Stellen Sie sicher, dass die Tabelle `catalogsearch_fulltext_cl` 15.000 IDs enthält.
1. Stellen Sie sicher, dass der `indexer_update_all_views` -Indexer ausgeführt wird.
1. Fordern Sie die Kategorieseite kontinuierlich an und beobachten Sie die Produktanzahl.

<u>Erwartete Ergebnisse</u>:

Die Produktanzahl sollte so bleiben, wie sie nach der Neuindizierung war.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt zählt nach einer Weile auf 7.450. Sie bleibt auch nach Abschluss der Indizierung in 7.450.

**2:**

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Bundle-Produkt mit einem zugehörigen einfachen Produkt als Option.
1. Ändern Sie die Indexmodi in *gemäß Plan aktualisieren*.
1. Weisen Sie das Bundle-Produkt einer Kategorie zu.
1. Ändern Sie den Lagerstatus des einfachen Produkts in *nicht vorrätig*.
1. Führen Sie Cron aus. Das Paket-Produkt verschwindet aus der Storefront.
1. Fügen Sie dem einfachen Produkt wieder Lager hinzu und speichern Sie.
1. Führen Sie den Cron-Indexer aus.
1. Aktualisieren Sie die Kategorieseite.

<u>Erwartete Ergebnisse</u>:

Das Produkt fehlt noch.

<u>Tatsächliche Ergebnisse</u>:

Das Bundle-Produkt wird wieder angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) verfügbare Patches.
