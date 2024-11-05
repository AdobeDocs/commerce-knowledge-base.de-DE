---
title: Live-Suchkatalog nicht synchronisiert
description: Dieser Artikel bietet Lösungen für das Adobe Commerce-Problem, bei dem Ihre Katalogdaten bei Verwendung der Live Search-Erweiterung nicht richtig synchronisiert werden.
exl-id: cd2e602f-b2c7-4ecf-874f-ec5f99ae1900
feature: Catalog Management, Search
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---

# Live-Suchkatalog nicht synchronisiert

Dieser Artikel bietet Lösungen für das Adobe Commerce-Problem, bei dem Ihre Katalogdaten bei Verwendung der Live Search-Erweiterung nicht richtig synchronisiert werden.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.x mit installierter Live Search-Erweiterung

## Problem

Ihre Katalogdaten werden nicht richtig synchronisiert oder ein neues Produkt wurde hinzugefügt, erscheint jedoch nicht in den Suchergebnissen.

>[!NOTE]
>
>Die Tabellennamen `catalog_data_exporter_products` und `catalog_data_exporter_product_attributes` werden jetzt als `cde_products_feed` und `cde_product_attributes_feed` ab [!DNL Live Search] Version 4.2.1 bezeichnet. Bei Händlern für Versionen vor 4.2.1 suchen Sie nach den Daten in den alten Tabellennamen, `catalog_data_exporter_products` und `catalog_data_exporter_product_attributes`.

<u>Zu reproduzierende Schritte</u>

1. Konfigurieren und verbinden Sie die Live-Suche für Ihre Adobe Commerce-Instanz, wie in der Benutzerdokumentation unter [Live-Suche installieren > API-Schlüssel konfigurieren](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#configure-api-keys) beschrieben.
1. Überprüfen Sie nach 30 Minuten die exportierten Katalogdaten, wie in unserer Benutzerdokumentation unter [Live-Suche installieren > Export überprüfen](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#verify-export) beschrieben.
1. Testen Sie die Verbindung nach 30 Minuten wie unter [Live-Suche installieren > Verbindung testen](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#test-connection) in unserer Benutzerdokumentation beschrieben.

Oder

1. Fügen Sie dem Katalog ein neues Produkt hinzu.
1. Versuchen Sie, eine Suchabfrage mit dem Produktnamen oder anderen durchsuchbaren Attributen nach 15-20 Minuten nach der Ausführung von Magento-Indexer + Cron auszuführen, um Daten mit dem Backend-Service zu synchronisieren.

<u>Erwartetes Ergebnis</u>

* Exportierte Katalogdaten können überprüft werden
* Verbindung erfolgreich hergestellt
* In den Suchergebnissen wird ein neues Produkt angezeigt.

<u>Tatsächliches Ergebnis</u>

Der exportierte Katalog kann nicht überprüft werden und/oder die Verbindung wird nicht hergestellt, da sich der API-Schlüssel geändert hat.

## Lösung

Es gibt verschiedene Möglichkeiten, die Probleme bei der Katalogsynchronisierung zu beheben.

### Warten Sie, bis die Änderungen übernommen wurden

Nach der Konfiguration und Verbindung kann es über 30 Minuten dauern, bis der Index in ES (Elasticsearch) erstellt und Suchergebnisse zurückgegeben werden. Nachfolgende einmalige Produktaktualisierungen werden voraussichtlich innerhalb weniger Minuten indiziert.

### Produktdaten für eine bestimmte SKU synchronisieren

Wenn Ihre Produktdaten für eine bestimmte SKU nicht richtig synchronisiert werden, gehen Sie wie folgt vor:

1. Verwenden Sie die folgende [!DNL SQL] -Abfrage und stellen Sie sicher, dass Sie über die in der Spalte `feed_data` erwarteten Daten verfügen. Notieren Sie sich auch den Zeitstempel `modified_at` .

   ```sql
   select * from cde_products_feed where sku = '<your_sku>' and store_view_code = '<your_ store_view_code>';
   ```

1. Wenn die korrekten Daten nicht angezeigt werden, versuchen Sie, die Neuindizierung mithilfe des folgenden Befehls durchzuführen und die [!DNL SQL] -Abfrage in Schritt 1 erneut auszuführen, um die Daten zu überprüfen:

   ```bash
   bin/magento indexer:reindex cde_products_feed
   ```

1. Wenn immer noch nicht die korrekten Daten angezeigt werden, erstellen Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).[

### Zeitstempel des letzten Produktexports überprüfen

1. Wenn die korrekten Daten in `cde_products_feed` angezeigt werden, verwenden Sie die folgende [!DNL SQL]-Abfrage, um den Zeitstempel des letzten Exports zu überprüfen. Sie sollte nach dem Zeitstempel `modified_at` liegen:

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. Wenn der Zeitstempel älter ist, können Sie mit dem folgenden Befehl entweder auf den nächsten Cron-Lauf warten oder ihn selbst Trigger haben:

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Warten Sie auf `<>` Zeit (Zeit für inkrementelle Aktualisierungen). Wenn Ihre Daten immer noch nicht angezeigt werden, erstellen Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).[

### Synchronisieren spezifischer Attributcode

Wenn Ihre Produktattributdaten für einen bestimmten Attributcode nicht richtig synchronisiert werden, gehen Sie wie folgt vor:

1. Verwenden Sie die folgende [!DNL SQL] -Abfrage und stellen Sie sicher, dass Sie über die in der Spalte `feed_data` erwarteten Daten verfügen. Notieren Sie sich auch den Zeitstempel `modified_at` .

   ```sql
   select * from cde_product_attributes_feed where json_extract(feed_data, '$.attributeCode') = '<your_attribute_code>' and store_view_code = '<your_ store_view_code>';
   ```

1. Wenn die korrekten Daten nicht angezeigt werden, verwenden Sie den folgenden Befehl, um die Neuindizierung vorzunehmen, und führen Sie dann die [!DNL SQL]-Abfrage in Schritt 1 erneut aus, um die Daten zu überprüfen.

   ```bash
   bin/magento indexer:reindex cde_product_attributes_feed
   ```

1. Wenn immer noch nicht die korrekten Daten angezeigt werden, erstellen Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).[

### Zeitstempel des letzten Produktattributexports überprüfen

Wenn die korrekten Daten in `cde_product_attributes_feed` angezeigt werden:

1. Verwenden Sie die folgende [!DNL SQL] -Abfrage, um den Zeitstempel des letzten Exports zu überprüfen. Sie sollte nach dem Zeitstempel `modified_at` liegen.

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. Wenn der Zeitstempel älter ist, können Sie mit dem folgenden Befehl entweder auf den nächsten Cron-Lauf warten oder ihn selbst Trigger haben:

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Warten Sie 15-20 Minuten (Zeit für inkrementelle Aktualisierungen). Wenn Ihre Daten immer noch nicht angezeigt werden, erstellen Sie bitte [ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Synchronisieren nach Änderung der API-Konfiguration

(Bekanntes Problem) Wenn Sie Ihre API-Konfiguration geändert haben, was zu einer Änderung Ihrer Data Space ID führt und feststellen kann, dass Ihre Katalogänderungen nicht mehr synchronisiert werden, führen Sie die folgenden Befehle aus:

```bash
bin/magento saas:resync --feed products
bin/magento saas:resync --feed productattributes
```

## Verwandtes Lesen

* [Onboard Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/onboarding-overview.html) in unserer Benutzerdokumentation
* [Überprüfen Sie die Protokolle und führen Sie eine Fehlerbehebung für den Datenexport und die Synchronisierung von Adobe Commerce SaaS durch](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging) im Adobe Commerce SaaS-Datenexport-Handbuch.
* [Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung
