---
title: "ACSD-53347: Die Leistung bei der Preisindizierung verschlechtert sich schrittweise im Zeitverlauf."
description: Wenden Sie den Patch ACSD-53347 an, um das Adobe Commerce-Problem zu beheben, bei dem sich die Leistung bei der Neuindizierung der Preise für einen großen Produktkatalog allmählich verschlechtert.
feature: Price Indexer
role: Admin
exl-id: 28795673-54b0-4282-bd43-344401cbe140
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-53347: Die Preisindexierungsleistung verschlechtert sich allmählich im Zeitverlauf

Der Patch ACSD-53347 behebt das Problem, bei dem sich die Leistung bei der Neuindizierung der Preise für einen großen Produktkatalog allmählich verschlechtert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 installiert ist. Die Patch-ID ist ACSD-53347. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Bei der Neuindizierung der Preise für einen großen Produktkatalog verschlechtert sich die Leistung der Abfragen, die während des Indizierungsprozesses ausgeführt werden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen großen einfachen Katalog und weisen Sie diesen Produkten benutzerdefinierte Optionen zu (benutzerdefinierte Optionen verwenden während der Indizierung eine temporäre Tabelle).
1. Erstellen Sie mindestens 200 Kundengruppen, um die Sichtbarkeit des Problems zu erhöhen.
1. Erstellen Sie zehn oder mehr Websites und weisen Sie ihnen alle Produkte zu.
1. Beachten Sie, dass die importierten Produkte fast identisch sind und sich nur nach SKU und Name unterscheiden.
1. Aktivieren Sie **[!UICONTROL DB Logging]**.
1. Führen Sie den Befehl `bin/magento index:reindex catalog_product_price` aus.
1. Suchen Sie in den `db.log` nach *DELETE VON`catalog_product_index_price_opt_agr_temp`*.

<u>Erwartete Ergebnisse</u>:

Die Ausführung der *DB-Abfragen* wird effizient ausgeführt.

<u>Tatsächliche Ergebnisse</u>:

Die Leistung der *DB-Abfragen* bei temporären Tabellen nimmt zu langsamen Zeitüberschreitungen zu, sodass die Preisindexierung viel Zeit in Anspruch nimmt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
