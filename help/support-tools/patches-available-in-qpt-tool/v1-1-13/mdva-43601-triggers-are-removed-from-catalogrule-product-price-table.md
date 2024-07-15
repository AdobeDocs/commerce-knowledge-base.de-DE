---
title: '"MDVA-43601: Trigger werden nach vollständiger Neuindizierung aus der Tabelle "catalogrule_product_price"entfernt.'
description: Der Patch MDVA-43601 behebt das Problem, dass Trigger nach einer vollständigen Neuindizierung von "catalogrule_rule_product_product"aus der Tabelle "catalogrule_price"entfernt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43601. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: fdef1e56-79ec-455a-8a29-b82f1c8ceea7
feature: Catalog Management, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-43601: Trigger werden nach vollständiger Neuindizierung aus der Tabelle &quot;catalogrule_product_price&quot;entfernt

Der Patch MDVA-43601 behebt das Problem, dass Trigger nach einer vollständigen Neuindizierung von `catalogrule_rule` oder `catalogrule_product` aus der Tabelle `catalogrule_product_price` entfernt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43601. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Trigger werden nach einer vollständigen Neuindizierung von `catalogrule_rule` oder `catalogrule_product` aus der `catalogrule_product_price`-Tabelle entfernt.

<u>Zu reproduzierende Schritte</u>:

1. Setzen Sie alle Indexer auf *Aktualisieren nach Zeitplan*.
1. Überprüfen Sie die für die Tabelle `catalogrule_product_price` erstellten Trigger, indem Sie die folgende SQL-Anforderung ausführen:

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. Manuelles Neuindizieren von `catalogrule_rule` oder `catalogrule_product` durch Ausführen des folgenden Befehls: `bin/magento indexer:reindex catalogrule_rule`
1. Überprüfen Sie erneut den Trigger der Tabelle &quot;`catalogrule_product_price`&quot;.

<u>Erwartete Ergebnisse</u>:

Trigger in der Tabelle &quot;`catalogrule_product_price`&quot; werden nach einer vollständigen Neuindizierung beibehalten.

<u>Tatsächliche Ergebnisse</u>:

Für die Tabelle `catalogrule_product_price` wurden keine Trigger gefunden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
