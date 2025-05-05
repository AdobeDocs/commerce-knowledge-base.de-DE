---
title: 'ACSD-51857: Langsamer Cron-Vorgang von „aggregate_sales_report_bestsellers_data“ wirkt sich auf die Leistung aus'
description: Wenden Sie den Patch ACSD-51857 an, um das Adobe Commerce-Problem zu beheben, bei dem der langsame Cron-Auftrag „aggregate_sales_report_bestsellers_data“ große Datenbanktabellen „sales_order“ und „sales_order_item“ betrifft.
exl-id: 444ab283-c98b-46b3-a492-706f0ce34a27
source-git-commit: a33364531d2efd572cd1b1847dd45e0f427af03b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51857: Langsamer Cron-Vorgang von `aggregate_sales_report_bestsellers_data` beeinträchtigt die Leistung

Der Patch ACSD-51857 behebt das Problem, dass langsame Cron-`aggregate_sales_report_bestsellers_data` große `sales_order` und `sales_order_item` Datenbanktabellen betreffen. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 installiert ist. Die Patch-ID ist ACSD-51857. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Cron-Auftragsleistung von `aggregate_sales_report_bestsellers_data` ist bei `sales_order` und `sales_order_item` Datenbanktabellen langsam.

Um dies zu beheben, wurde die Hauptdatenabfrage, die Daten für den Bericht erfasst, in eine effizientere Form umgeschrieben. Jetzt wird eine Unterabfrage verwendet, um eine Teilmenge der Daten zu bestimmen.

Damit die Unterabfrage so schnell wie möglich funktioniert, wurde ein neuer Index für die `sales_order` Datenbanktabelle hinzugefügt: `SALES_ORDER_STORE_STATE_CREATED` basierend auf `store_id`-, `state`- und `created_at`.

<u>Voraussetzungen</u>

Stellen Sie eine große Anzahl von Bestellungen täglich sicher.

<u>Schritte zur Reproduktion</u>

1. Führen Sie den `aggregate_sales_report_bestsellers_data` Cron-Auftrag aus.
1. Markieren Sie die Daten, die im Admin-Dashboard unter der Registerkarte **[!UICONTROL Bestsellers]** angezeigt werden sollen.

<u>Erwartete Ergebnisse</u>:

*[!UICONTROL Quantity per source]* unter der Registerkarte **[!UICONTROL Configuration]** darf nicht leer sein.

<u>Tatsächliche Ergebnisse</u>:

*[!UICONTROL Quantity per source]* unter der Registerkarte **[!UICONTROL Configuration]** ist leer.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
