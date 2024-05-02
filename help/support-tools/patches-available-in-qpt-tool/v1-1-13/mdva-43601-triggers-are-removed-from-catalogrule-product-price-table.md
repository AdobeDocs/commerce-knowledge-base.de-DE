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

Der Patch MDVA-43601 behebt das Problem, dass Trigger aus entfernt werden `catalogrule_product_price` nach einer vollständigen Neuindizierung von `catalogrule_rule` oder `catalogrule_product`. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43601. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Trigger werden aus `catalogrule_product_price` nach einer vollständigen Neuindizierung von `catalogrule_rule` oder `catalogrule_product`.

<u>Zu reproduzierende Schritte</u>:

1. Setzen Sie alle Indexer auf *Nach Zeitplan aktualisieren*.
1. Überprüfen Sie die für erstellten Trigger. `catalogrule_product_price` -Tabelle durch Ausführen der folgenden SQL-Anforderung:

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. Manuelle Neuindizierung `catalogrule_rule` oder `catalogrule_product` durch Ausführen des folgenden Befehls: `bin/magento indexer:reindex catalogrule_rule`
1. Überprüfen Sie den Trigger von `catalogrule_product_price` erneut auszufüllen.

<u>Erwartete Ergebnisse</u>:

Trigger in `catalogrule_product_price` -Tabelle wird nach einer vollständigen Neuindizierung beibehalten.

<u>Tatsächliche Ergebnisse</u>:

Es wurden keine Trigger für `catalogrule_product_price` Tabelle.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
