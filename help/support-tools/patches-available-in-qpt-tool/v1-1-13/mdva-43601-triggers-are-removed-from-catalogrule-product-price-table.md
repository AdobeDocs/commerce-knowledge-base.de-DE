---
title: 'MDVA-43601: Trigger werden nach vollständiger Neuindizierung aus der Tabelle „catalogrule_product_price“ entfernt'
description: Der Patch MDVA-43601 behebt das Problem, dass Trigger aus der Tabelle „catalogrule_product_price“ nach einer vollständigen Neuindizierung von „catalogrule_rule“ oder „catalogrule_product“ entfernt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43601. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: fdef1e56-79ec-455a-8a29-b82f1c8ceea7
feature: Catalog Management, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-43601: Trigger werden nach vollständiger Neuindizierung aus der Tabelle „catalogrule_product_price“ entfernt

Der Patch MDVA-43601 behebt das Problem, dass Trigger nach einer vollständigen Neuindizierung von `catalogrule_rule` oder `catalogrule_product` aus `catalogrule_product_price` Tabelle entfernt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43601. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Trigger werden nach einer vollständigen Neuindizierung von `catalogrule_rule` oder `catalogrule_product` aus `catalogrule_product_price` Tabelle entfernt.

<u>Schritte zur Reproduktion</u>:

1. Setzen Sie alle Indexer auf *Nach Zeitplan aktualisieren*.
1. Überprüfen Sie die für `catalogrule_product_price` Tabelle erstellten Trigger, indem Sie die folgende SQL-Anfrage ausführen:

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. Indizieren Sie `catalogrule_rule` oder `catalogrule_product` manuell neu, indem Sie den folgenden Befehl ausführen: `bin/magento indexer:reindex catalogrule_rule`
1. Überprüfen Sie die Trigger `catalogrule_product_price` Tabelle erneut.

<u>Erwartete Ergebnisse</u>:

Trigger in `catalogrule_product_price` Tabelle bleiben nach einer vollständigen Neuindizierung erhalten.

<u>Tatsächliche Ergebnisse</u>:

Für `catalogrule_product_price` Tabelle wurden keine Trigger gefunden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
