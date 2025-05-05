---
title: 'ACSD-56415: Leistung von [!UICONTROL Partial Price Indexing] aufgrund der Abfrage "DELETE" verlangsamt'
description: Wenden Sie den Patch ACSD-56415 an, um das Adobe Commerce-Problem zu beheben, bei dem die Leistung des [!UICONTROL Partial Price Indexing] aufgrund einer "DELETE"-Abfrage verlangsamt wird, wenn die Datenbank viele partielle Preisdaten zu indizieren hat.
feature: Catalog Service
role: Admin, Developer
exl-id: 0b099570-9f27-4ae2-9384-6b69ea50bd98
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-56415: Die [!UICONTROL Partial Price Indexing] ist aufgrund `DELETE` Abfrage verlangsamt

Mit dem Patch ACSD-56415 wird das Problem behoben, dass die Leistung der [!UICONTROL Partial Price Indexing] aufgrund einer `DELETE`-Abfrage verlangsamt wird, wenn die Datenbank viele partielle Preisdatenindizes hat. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 installiert ist. Die Patch-ID ist ACSD-56023. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Leistung von [!UICONTROL Partial Price Indexing] wird aufgrund einer `DELETE` Abfrage verlangsamt, wenn die Datenbank viele partielle Preisdatenindizes hat.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie *300000 Produkte* und *10-Websites* dem großen Leistungsprofil.
1. Melden Sie sich beim Admin Panel an.
1. Erstellen Sie *10 Kundengruppen*.
1. Führen Sie die folgende Abfrage aus, um Produkte zur `_cl`-Tabelle hinzuzufügen:

   &grave;&grave;
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 &grave;&grave;

1. Führen Sie den folgenden Befehl aus, um den partiellen Preisindizierungsprozess Trigger:

   &grave;&grave;
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 &grave;&grave;

<u>Erwartete Ergebnisse</u>:

Das SQL-Abfrage-DELETE `main_table` FROM `catalog_product_index_price` wird schnell ausgeführt.

<u>Tatsächliche Ergebnisse</u>:

Das SQL-Abfrage-DELETE `main_table` FROM `catalog_product_index_price` wird nur sehr langsam ausgeführt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
