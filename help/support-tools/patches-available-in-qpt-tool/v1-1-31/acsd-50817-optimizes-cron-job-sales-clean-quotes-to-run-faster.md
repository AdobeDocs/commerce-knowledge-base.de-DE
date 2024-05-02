---
title: "ACSD-50817: Optimiert cron job sales_clean_quotes für schnellere Ausführung"
description: Wenden Sie den Patch ACSD-50817 an, um den Cron-Auftrag `sales_clean_quotes` so zu optimieren, dass er schneller ausgeführt wird, indem Sie einen zusammengesetzten Index zu den Spalten "store_id"und "updated_at"in der Anführungszeichentabelle hinzufügen.
exl-id: b08b12ff-37ac-4a7d-bce2-2a27e4f916f0
feature: Quotes
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-50817: Optimiert den Cron-Auftrag `sales_clean_quotes` schnellere Ausführung

Der Patch ACSD-50817 optimiert den Cron-Auftrag `sales_clean_quotes` um schneller zu laufen, indem Sie einen zusammengesetzten Index für die `store_id` und `updated_at` Spalten in der Anführungszeichentabelle. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.31 installiert ist. Die Patch-ID lautet ACSD-50817.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Cron-Auftrag `sales_clean_quotes` ist zu langsam. Mit diesem Patch wurde er für eine schnellere Ausführung optimiert, indem ein zusammengesetzter Index zur `store_id` und `updated_at` Spalten in der Anführungszeichentabelle.

<u>Zu reproduzierende Schritte</u>:

1. Generieren von 50-80 MB Anführungszeichen mit `updated_at` auf &lt; 30 Tage eingestellt ist.
1. Ausführen des Cron-Auftrags `sales_clean_quotes` oder die folgende Abfrage in der Anführungszeichentabelle:

   ```cron
   SELECT COUNT(*) FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0')
   
   SELECT * FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0') LIMIT 50
   ```

<u>Erwartete Ergebnisse</u>

Cron-Auftrag `sales_clean_quotes` ist für eine schnellere Ausführung optimiert, indem ein zusammengesetzter Index zur `store_id` und `updated_at` Spalten in der Anführungszeichentabelle.

<u>Tatsächliche Ergebnisse</u>

Die Abfrage ist zu langsam.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
