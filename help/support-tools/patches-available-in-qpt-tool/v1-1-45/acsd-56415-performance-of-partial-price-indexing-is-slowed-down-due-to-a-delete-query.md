---
title: '"ACSD-56415: Leistung von [!UICONTROL Partial Price Indexing] verlangsamt aufgrund der Abfrage "DELETE"'
description: Wenden Sie den Patch ACSD-56415 an, um das Adobe Commerce-Problem zu beheben, bei dem die Leistung der [!UICONTROL Partial Price Indexing] aufgrund einer "DELETE"-Abfrage verlangsamt wird, wenn die Datenbank über viele partielle Preisdaten verfügt, die indiziert werden sollen.
feature: Catalog Service
role: Admin, Developer
exl-id: 0b099570-9f27-4ae2-9384-6b69ea50bd98
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-56415: Leistung von [!UICONTROL Partial Price Indexing] wird aufgrund von `DELETE` Abfrage

Der Patch ACSD-56415 behebt das Problem, bei dem die Leistung der [!UICONTROL Partial Price Indexing] wird aufgrund einer `DELETE` abfragen, wenn die Datenbank über einen großen Teil des Preisdatenindex verfügt. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 ist installiert. Die Patch-ID ist ACSD-56023. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Leistung von [!UICONTROL Partial Price Indexing] wird aufgrund einer `DELETE` abfragen, wenn die Datenbank über einen großen Teil des Preisdatenindex verfügt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen *300000 Erzeugnisse* und *10 Websites* unter Verwendung des großen Leistungsprofils.
1. Melden Sie sich beim Admin Panel an.
1. Erstellen *10 Kundengruppen*.
1. Führen Sie die folgende Abfrage aus, um Produkte zum `_cl` table:

   ``
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 ``

1. Führen Sie den folgenden Befehl aus, um die partielle Preisindizierung Trigger:

   ``
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 ``

<u>Erwartete Ergebnisse</u>:

Das SQL-Abfrage-DELETE `main_table` VON `catalog_product_index_price` schnell ausgeführt wird.

<u>Tatsächliche Ergebnisse</u>:

Das SQL-Abfrage-DELETE `main_table` VON `catalog_product_index_price` wird sehr langsam ausgeführt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
