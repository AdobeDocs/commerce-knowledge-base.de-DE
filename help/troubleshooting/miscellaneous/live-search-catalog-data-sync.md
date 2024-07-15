---
title: Live-Suchkatalog nicht synchronisiert
description: Dieser Artikel bietet Lösungen für das Adobe Commerce-Problem, bei dem Ihre Katalogdaten bei Verwendung der Live Search-Erweiterung nicht richtig synchronisiert werden.
exl-id: cd2e602f-b2c7-4ecf-874f-ec5f99ae1900
feature: Catalog Management, Search
role: Developer
source-git-commit: a1b049dab989d5d8594d86b64b778e6e277a9f41
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 0%

---

# Live-Suchkatalog nicht synchronisiert

Dieser Artikel bietet Lösungen für das Adobe Commerce-Problem, bei dem Ihre Katalogdaten bei Verwendung der Live Search-Erweiterung nicht richtig synchronisiert werden.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.x mit installierter Live Search-Erweiterung

## Problem

Ihre Katalogdaten werden nicht richtig synchronisiert oder ein neues Produkt wurde hinzugefügt, erscheint aber nicht in den Suchergebnissen.

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

1. Verwenden Sie die folgende SQL-Abfrage und stellen Sie sicher, dass Sie über die erwarteten Daten in der Spalte `feed_data` verfügen. Notieren Sie sich auch den Zeitstempel `modified_at` .

   ```sql
   select * from catalog_data_exporter_products where sku = '<your_sku>' and store_view_code = '<your_ store_view_code>';
   ```

1. Wenn die korrekten Daten nicht angezeigt werden, versuchen Sie, die Neuindizierung mit dem folgenden Befehl durchzuführen und führen Sie die SQL-Abfrage in Schritt 1 erneut aus, um die Daten zu überprüfen:

   ```bash
   bin/magento indexer:reindex catalog_data_exporter_products
   ```

1. Wenn immer noch nicht die korrekten Daten angezeigt werden, erstellen Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).[

### Zeitstempel des letzten Produktexports überprüfen

1. Wenn die korrekten Daten in `catalog_data_exporter_products` angezeigt werden, verwenden Sie die folgende SQL-Abfrage, um den Zeitstempel des letzten Exports zu überprüfen. Sie sollte nach dem Zeitstempel `modified_at` liegen:

   ```sql
   select * from flag where flag_code = 'products-feed-version';
   ```

1. Wenn der Zeitstempel älter ist, können Sie mit dem folgenden Befehl entweder auf den nächsten Cron-Lauf warten oder ihn selbst Trigger haben:

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Warten Sie auf `<>` Zeit (Zeit für inkrementelle Aktualisierungen). Wenn Ihre Daten immer noch nicht angezeigt werden, erstellen Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).[

### Synchronisieren spezifischer Attributcode

Wenn Ihre Produktattributdaten für einen bestimmten Attributcode nicht richtig synchronisiert werden, gehen Sie wie folgt vor:

1. Verwenden Sie die folgende SQL-Abfrage und stellen Sie sicher, dass Sie über die erwarteten Daten in der Spalte `feed_data` verfügen. Notieren Sie sich auch den Zeitstempel `modified_at` .

   ```sql
   select * from catalog_data_exporter_product_attributes where json_extract(feed_data, '$.attributeCode') = '<your_attribute_code>' and store_view_code = '<your_ store_view_code>';
   ```

1. Wenn die korrekten Daten nicht angezeigt werden, verwenden Sie den folgenden Befehl, um die SQL-Abfrage neu zu indizieren, und führen Sie dann die SQL-Abfrage in Schritt 1 erneut aus, um die Daten zu überprüfen.

   ```bash
   bin/magento indexer:reindex catalog_data_exporter_product_attributes
   ```

1. Wenn immer noch nicht die korrekten Daten angezeigt werden, erstellen Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).[

### Zeitstempel des letzten Produktattributexports überprüfen

Wenn die korrekten Daten in `catalog_data_exporter_product_attributes` angezeigt werden:

1. Verwenden Sie die folgende SQL-Abfrage, um den Zeitstempel des letzten Exports zu überprüfen. Sie sollte nach dem Zeitstempel `modified_at` liegen.

   ```sql
   select * from flag where flag_code = 'product-attributes-feed-version';
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

Siehe [Onboard Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/onboarding-overview.html) in unserer Benutzerdokumentation.
