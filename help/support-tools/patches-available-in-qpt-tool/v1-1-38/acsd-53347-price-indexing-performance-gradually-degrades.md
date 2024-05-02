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

Der Patch ACSD-53347 behebt das Problem, bei dem sich die Leistung bei der Neuindizierung der Preise für einen großen Produktkatalog allmählich verschlechtert. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 installiert ist. Die Patch-ID ist ACSD-53347. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Bei der Neuindizierung der Preise für einen großen Produktkatalog verschlechtert sich die Leistung der Abfragen, die während des Indizierungsprozesses ausgeführt werden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen großen einfachen Katalog und weisen Sie diesen Produkten benutzerdefinierte Optionen zu (benutzerdefinierte Optionen verwenden während der Indizierung eine temporäre Tabelle).
1. Erstellen Sie mindestens 200 Kundengruppen, um die Sichtbarkeit des Problems zu erhöhen.
1. Erstellen Sie zehn oder mehr Websites und weisen Sie ihnen alle Produkte zu.
1. Beachten Sie, dass die importierten Produkte fast identisch sind und sich nur nach SKU und Name unterscheiden.
1. Aktivieren **[!UICONTROL DB Logging]**.
1. Führen Sie die `bin/magento index:reindex catalog_product_price` Befehl.
1. Suchen Sie nach *DELETE VON`catalog_product_index_price_opt_agr_temp`* im `db.log`.

<u>Erwartete Ergebnisse</u>:

Die Ausführung der *DB-Abfragen* effizient ausgeführt werden.

<u>Tatsächliche Ergebnisse</u>:

Die Leistung der *DB-Abfragen* auf temporären Tabellen werden zu langsamen Überstunden, sodass die Preisindexierung viel Zeit in Anspruch nimmt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
