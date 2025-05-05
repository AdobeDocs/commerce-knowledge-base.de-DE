---
title: 'ACSD-58739: Bei der partiellen Neuindizierung wird ein Fehler ausgegeben'
description: Wenden Sie den Patch ACSD-55241 an, um das Adobe Commerce-Problem zu beheben, bei dem eine partielle Neuindizierung einen Fehler auslöst.
feature: Inventory, Products
role: Admin, Developer
exl-id: 19f177f4-054b-4593-970b-7cbf04710bef
source-git-commit: 06f751e43ef825c0eb29cb9b42eb41f07c308625
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# ACSD-58739: Bei der partiellen Neuindizierung wird ein Fehler ausgegeben

Der Patch ACSD-58739 behebt das Problem, dass die partielle Neuindizierung einen Fehler auslöst. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 installiert ist. Die Patch-ID ist ACSD-58739. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die partielle Neuindizierung gibt einen Fehler aus.

<u>Schritte zur Reproduktion</u>:

1. Slave-Verbindungseinstellungen zum `app/etc/ev.php` hinzufügen.
1. Generieren Sie bis zu 10000 Produkte und führen Sie den folgenden Befehl aus:

   ```
   bin/magento index:reindex
   ```

1. Hinzufügen generierter Produkt-IDs in `catalogsearch_fulltext_cl` DB-Tabelle.

   ```
   insert into catalogsearch_fulltext_cl (entity_id) select entity_id from catalog_product_entity;
   ```

1. Führen Sie den folgenden Befehl aus, um die partielle Neuindizierung Trigger:

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1 
   ```

1. Überprüfen Sie die `var/log/support_report.log`.

<u>Erwartete Ergebnisse</u>

Kein Fehler.

<u>Tatsächliche Ergebnisse</u>:

*Basistabelle oder -ansicht nicht gefunden* tritt bei der Ausführung einer partiellen Neuindizierung ein Fehler auf.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
