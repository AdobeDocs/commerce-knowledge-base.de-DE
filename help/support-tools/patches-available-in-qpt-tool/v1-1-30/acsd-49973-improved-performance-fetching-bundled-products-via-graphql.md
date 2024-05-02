---
title: '"ACSD-49973: Verbesserte Leistung beim Abrufen von gebündelten Produkten über [!DNL GraphQL]'''
description: Wenden Sie den Patch ACSD-49973 an, um das Adobe Commerce-Problem zu beheben, bei dem die Leistung beim Abrufen gebündelter Produkte über beeinträchtigt wird. [!DNL GraphQL].
exl-id: 7d7fce0f-40f9-4dec-aee7-1014690ccd7c
feature: GraphQL, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# ACSD-49973: Verbesserte Leistung beim Abrufen von gebündelten Produkten über [!DNL GraphQL]

Der Patch ACSD-49973 verbessert die Leistung beim Abrufen von gebündelten Produkten über [!DNL GraphQL]. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 installiert ist. Die Patch-ID lautet ACSD-49973. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Leistung wird beim Abrufen gebündelter Produkte über reduziert [!DNL GraphQL].

<u>Voraussetzungen</u>:

Erstellen Sie 2000 Bundle-Produkte mit dem [Leistungs-Tool](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html).

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie die [!DNL DB] Abfragelogger:

   ```
   bin/magento dev:query-log:enable
   ```

1. Führen Sie Folgendes aus [!DNL GraphQL] Abfrage:

   ```GraphQL
   {
     products(
       search: "bundle"
       pageSize: 2000,
       sort: { relevance: DESC }
     ) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. Überprüfen `var/log/db.log` für Anfragen an `catalog_product_bundle_selection` Tabelle.

<u>Erwartete Ergebnisse</u>:

Anforderungen an `catalog_product_bundle_selection` -Tabelle sollte nicht im `var/log/db.log`.

<u>Tatsächliche Ergebnisse</u>:

Es gibt 2000 Anfragen an `catalog_product_bundle_selection` -Tabelle, die gleichzeitig ausgelöst wird und die Leistungsbeeinträchtigung verursacht.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
