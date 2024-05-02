---
title: '"ACSD-51857: Langsamer Cron-Auftrag von "aggregate_sales_report_bestsellers_data"wirkt sich auf die Leistung aus.'
description: Wenden Sie den Patch ACSD-51857 an, um das Adobe Commerce-Problem zu beheben, bei dem der langsame Cron-Auftrag "aggregate_sales_report_bestsellers_data"große Datenbanktabellen "sales_order"und "sales_order_item"betrifft.
exl-id: 444ab283-c98b-46b3-a492-706f0ce34a27
source-git-commit: a33364531d2efd572cd1b1847dd45e0f427af03b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51857: Langsamer Cron-Auftrag von `aggregate_sales_report_bestsellers_data` beeinträchtigt die Leistung

Der Patch ACSD-51857 behebt das Problem, dass langsamer Cron-Auftrag `aggregate_sales_report_bestsellers_data` betrifft große `sales_order` und `sales_order_item` Datenbanktabellen. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 ist installiert. Die Patch-ID ist ACSD-51857. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Cron-Auftragsleistung `aggregate_sales_report_bestsellers_data` ist langsam ein `sales_order` und `sales_order_item` Datenbanktabellen.

Um dies zu beheben, wurde die Hauptdatenabfrage, die Daten für den Bericht abruft, in ein effizienteres Formular umgeschrieben. Jetzt wird eine Unterabfrage verwendet, um die Datenuntergruppe zu bestimmen.

Damit die Unterabfrage so schnell wie möglich funktioniert, wurde ein neuer Index für die `sales_order` Datenbanktabelle: `SALES_ORDER_STORE_STATE_CREATED` basierend auf `store_id`, `state`, und `created_at` Spalten.

<u>Voraussetzungen</u>

Stellen Sie täglich eine große Anzahl von Bestellungen sicher.

<u>Zu reproduzierende Schritte</u>

1. Führen Sie die `aggregate_sales_report_bestsellers_data` Cron-Auftrag.
1. Überprüfen Sie die Daten, die im Admin-Dashboard angezeigt werden sollen, unter dem **[!UICONTROL Bestsellers]** Registerkarte.

<u>Erwartete Ergebnisse</u>:

*[!UICONTROL Quantity per source]* unter **[!UICONTROL Configuration]** -Registerkarte sollte nicht leer sein.

<u>Tatsächliche Ergebnisse</u>:

*[!UICONTROL Quantity per source]* unter **[!UICONTROL Configuration]** ist leer.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
