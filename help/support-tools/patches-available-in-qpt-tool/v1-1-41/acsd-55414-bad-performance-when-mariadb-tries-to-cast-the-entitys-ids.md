---
title: "ACSD-55414: Schlechte Leistung, wenn MariaDB versucht, die entitys_ids zu übertragen."
description: Wenden Sie den Patch ACSD-55414 an, um das Adobe Commerce-Problem zu beheben, wenn die MariaDB versucht, "entitys_ids"aus Zeichenfolge in Ganzzahl zu konvertieren. Dadurch wird die Neuindizierung behindert.
feature: Attributes
role: Admin, Developer
exl-id: 008a4fda-5d80-47e2-8fb4-c1e39d15a6ba
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-55414: Schlechte Leistung, wenn MariaDB versucht, die `entitys_ids`

Der Patch ACSD-55414 behebt das Problem, bei dem die Leistung der Neuindizierung beeinträchtigt wird, wenn die MariaDB versucht, eine Konvertierung vorzunehmen `entitys_ids` von Zeichenfolge zu Ganzzahl. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.41 installiert ist. Die Patch-ID ist ACSD-55414. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Neuindizierung wird behindert, wenn die MariaDB versucht, die `entitys_ids` von Zeichenfolge zu Ganzzahl.

<u>Zu reproduzierende Schritte</u>:

1. Aktualisieren `setup/performance-toolkit/profiles/ce/small.xml` durch Einrichtung *50000* einfache Produkte.
1. Generieren Sie dieses Profil durch Ausführen des Befehls: `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Führen Sie reindex aus: `bin/magento indexer:reindex catalog_product_attribute`.

<u>Erwartete Ergebnisse</u>:

Der Abschluss der Neuindizierung dauert vernünftig.

<u>Tatsächliche Ergebnisse</u>:

Der Abschluss der Neuindizierung dauert zu lange.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
