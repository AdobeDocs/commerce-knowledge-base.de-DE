---
title: "MDVA-33382 Patch: invalidierte Indexer"
description: Der Patch MDVA-3382 behebt das Problem, wenn Indexer nach dem Hinzufügen, Entfernen oder Neuanordnen von Produkten in einer Kategorie invalidiert werden. Die ungültigen Indexer sind "catalog_category_product" , "catalogsearch_fulltext"(und ihre abhängigen Elemente).
exl-id: b4ac10ee-0f9d-4d7a-be72-c4d90ebadb10
feature: Catalog Management, Categories, Price Indexer
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# MDVA-33382 Patch: invalidierte Indexer

Der Patch MDVA-3382 behebt das Problem, wenn Indexer nach dem Hinzufügen, Entfernen oder Neuanordnen von Produkten in einer Kategorie invalidiert werden. Die Indexer, die invalidiert werden, sind `catalog_category_product` , `catalogsearch_fulltext` (und ihre abhängigen Elemente).

Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce für die Cloud-Infrastruktur 2.3.4-p2

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce in der Cloud-Infrastruktur und Adobe Commerce On-Premise 2.3.0 - 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Setzen Sie alle Indizes für Indexermodi auf **Planmäßig aktualisieren**.
1. Entfernen Sie ein Produkt aus einer Kategoriebearbeitungsseite.
1. Speichern Sie die Kategorie.
1. Überprüfen Sie den Indexstatus entweder im Backend oder in der CLI.

<u>Erwartete Ergebnisse</u>:

Die folgenden Indizes werden nicht invalidiert: `catalog_category_product` , `catalogsearch_fulltext` (und ihre abhängigen Elemente), wie erwartet.

<u>Tatsächliche Ergebnisse</u>:

Die folgenden Indizes werden ungültig gemacht: `catalog_category_product` , `catalogsearch_fulltext` (und ihre abhängigen Elemente).

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie in der [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
