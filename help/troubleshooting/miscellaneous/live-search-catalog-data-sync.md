---
title: Live Search-Katalog nicht synchronisiert
description: Dieser Artikel bietet Lösungen für das Adobe Commerce-Problem, bei dem Ihre Katalogdaten bei Verwendung der Live Search-Erweiterung nicht korrekt synchronisiert werden.
exl-id: cd2e602f-b2c7-4ecf-874f-ec5f99ae1900
feature: Catalog Management, Search
role: Developer
source-git-commit: 5911b436fdcc08e695fb14d35784287945593815
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# Live Search-Katalog nicht synchronisiert

Dieser Artikel bietet Lösungen für das Adobe Commerce-Problem, bei dem Ihre Katalogdaten bei Verwendung der Live Search-Erweiterung nicht korrekt synchronisiert werden.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.x mit installierter Live Search-Erweiterung

## Problem

Ihre Katalogdaten werden nicht korrekt synchronisiert oder es wurde ein neues Produkt hinzugefügt, es wird jedoch nicht in den Suchergebnissen angezeigt. Möglicherweise wird auch die folgende Fehlermeldung in der `var/log/exception.log` angezeigt:

`Magento_LiveSearch: An error occurred in search backend. {"result":{"errors":[{"message":"Exception while fetching data (/productSearch) : No index was found for this request"}]}}`

>[!NOTE]
>
>Die Tabellennamen `catalog_data_exporter_products` und `catalog_data_exporter_product_attributes` werden ab [!DNL Live Search] Version 4.2.1 nun `cde_products_feed` und `cde_product_attributes_feed` genannt. Händler, die mit Versionen vor 4.2.1 arbeiten, suchen nach den Daten in den alten Tabellennamen, `catalog_data_exporter_products` und `catalog_data_exporter_product_attributes`.

<u>Schritte zur Reproduktion</u>

1. Konfigurieren und verbinden Sie die Live Search für Ihre Adobe Commerce-Instanz, wie in [Live Search installieren > API-Schlüssel konfigurieren](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=de#configure-api-keys) in unserer Benutzerdokumentation beschrieben.
1. Überprüfen Sie nach 30 Minuten die exportierten Katalogdaten, wie unter [Live-Suche installieren > Export überprüfen](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=de#verify-export) in unserer Benutzerdokumentation beschrieben.
1. Testen Sie nach 30 Minuten die Verbindung, wie unter [Live Search installieren > Verbindung testen](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=de#test-connection) in unserer Benutzerdokumentation beschrieben.

Or

1. Fügen Sie ein neues Produkt zum Katalog hinzu.
1. Versuchen Sie, eine Suchabfrage mit dem Produktnamen oder anderen durchsuchbaren Attributen auszuführen, nachdem 15-20 Minuten nach dem Zeitpunkt, zu dem Magento Indexer + Cron ausgeführt wurden, um Daten mit dem Backend-Service zu synchronisieren.

<u>Erwartetes Ergebnis</u>

* Exportierte Katalogdaten können überprüft werden
* Verbindung erfolgreich
* Neues Produkt wird in den Suchergebnissen angezeigt.

<u>Tatsächliches Ergebnis</u>

Exportierte Kataloge können nicht verifiziert werden und/oder die Verbindung wurde nicht hergestellt, da sich der API-Schlüssel geändert hat.

## Lösung

Es gibt mehrere Möglichkeiten, die Katalogsynchronisierungsprobleme zu beheben.

### Auf die Anwendung von Änderungen warten

Nachdem Sie konfiguriert und eine Verbindung hergestellt haben, kann es über 30 Minuten dauern, bis der Index in ES (Elasticsearch) erstellt und Suchergebnisse zurückgegeben werden. Nachfolgende einmalige Produktaktualisierungen werden voraussichtlich innerhalb weniger Minuten indiziert.

### Synchronisieren von Produktdaten für eine bestimmte SKU

Wenn Ihre Produktdaten für eine bestimmte SKU nicht korrekt synchronisiert werden, gehen Sie wie folgt vor:

1. Verwenden Sie die folgende [!DNL SQL]-Abfrage und stellen Sie sicher, dass die erwarteten Daten in der Spalte `feed_data` vorhanden sind. Notieren Sie sich auch den `modified_at` Zeitstempel.

   ```sql
   SELECT * FROM cde_products_feed WHERE json_extract(feed_data, '$.sku') = '<your_sku>' AND json_extract(feed_data, '$.storeViewCode') = '<your_ store_view_code>';
   ```

   Beispiel:

   ```sql
   SELECT * FROM cde_products_feed WHERE json_extract(feed_data, '$.sku') = '24-MB04' AND json_extract(feed_data, '$.storeViewCode') = 'default';
   ```

1. Wenn nicht die richtigen Daten angezeigt werden, versuchen Sie, die Neuindizierung mit dem folgenden Befehl durchzuführen und führen Sie die [!DNL SQL] Abfrage in Schritt 1 erneut aus, um die Daten zu überprüfen:

   ```bash
   bin/magento indexer:reindex cde_products_feed
   ```

1. Wenn immer noch nicht die richtigen Daten angezeigt werden, erstellen [&#x200B; ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Zeitstempel des letzten Produktexports überprüfen

1. Wenn in `cde_products_feed` die richtigen Daten angezeigt werden, verwenden Sie die folgende [!DNL SQL]-Abfrage, um den Zeitstempel des letzten Exports zu überprüfen. Er sollte nach dem `modified_at` Zeitstempel liegen:

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. Wenn der Zeitstempel älter ist, können Sie entweder auf die nächste Cron-Ausführung warten oder ihn mithilfe des folgenden Befehls selbst Trigger machen:

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Warten Sie `<>` (Zeit für inkrementelle Aktualisierungen). Wenn Ihre Daten weiterhin nicht angezeigt werden, erstellen [&#x200B; ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Spezifischen Attributcode synchronisieren

Wenn Ihre Produktattributdaten für einen bestimmten Attributcode nicht korrekt synchronisiert sind, gehen Sie wie folgt vor:

1. Verwenden Sie die folgende [!DNL SQL]-Abfrage und stellen Sie sicher, dass die erwarteten Daten in der Spalte `feed_data` vorhanden sind. Notieren Sie sich auch den `modified_at` Zeitstempel.

   ```sql
   select * from cde_product_attributes_feed where json_extract(feed_data, '$.attributeCode') = '<your_attribute_code>' and store_view_code = '<your_ store_view_code>';
   ```

1. Wenn nicht die richtigen Daten angezeigt werden, verwenden Sie den folgenden Befehl, um die Daten neu zu indizieren, und führen Sie dann die [!DNL SQL] Abfrage in Schritt 1 erneut aus, um die Daten zu überprüfen.

   ```bash
   bin/magento indexer:reindex cde_product_attributes_feed
   ```

1. Wenn immer noch nicht die richtigen Daten angezeigt werden, erstellen [&#x200B; ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Zeitstempel des letzten Produktattribut-Exports überprüfen

Wenn die richtigen Daten in `cde_product_attributes_feed` angezeigt werden:

1. Verwenden Sie die folgende [!DNL SQL]-Abfrage, um den Zeitstempel des letzten Exports zu überprüfen. Er sollte nach dem `modified_at` Zeitstempel liegen.

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. Wenn der Zeitstempel älter ist, können Sie entweder auf die nächste Cron-Ausführung warten oder ihn mithilfe des folgenden Befehls selbst Trigger machen:

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. 15-20 Minuten warten (Zeit für inkrementelle Aktualisierungen). Wenn Ihre Daten weiterhin nicht angezeigt werden, erstellen [&#x200B; ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Nach API-Konfigurationsänderung synchronisieren

(Bekanntes Problem) Wenn Sie Ihre API-Konfiguration geändert haben, was zu einer Änderung Ihrer Datenraum-ID führt, und feststellen, dass Ihre Katalogänderungen nicht mehr synchronisiert werden, führen Sie die folgenden Befehle aus, um die Feeds neu zu synchronisieren:

```
bin/magento saas:resync --feed productattributes --cleanup-feed
bin/magento saas:resync --feed products --cleanup-feed
bin/magento saas:resync --feed scopesCustomerGroup --cleanup-feed
bin/magento saas:resync --feed scopesWebsite --cleanup-feed
bin/magento saas:resync --feed prices --cleanup-feed
bin/magento saas:resync --feed productOverrides --cleanup-feed
bin/magento saas:resync --feed variants --cleanup-feed
bin/magento saas:resync --feed categories --cleanup-feed
bin/magento saas:resync --feed categoryPermissions --cleanup-feed
```

[Senden einer Support-Anfrage](https://experienceleague.adobe.com/home?lang=de&support-tab=home#support) um eine Neuindizierung des Live Search-Index anzufordern. Geben Sie in der Problembeschreibung Ihre Datenspeicher-/Umgebungs-ID ein, die Sie im Admin-Bedienfeld unter **[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Commerce Services Connector]** finden.

>[!IMPORTANT]
>Die Verwendung der Option `--cleanup-feed` in anderen Fällen kann zu Datenverlust und Problemen mit der Datensynchronisation führen.  Verwenden Sie sie nur, wenn Sie eine neue, leere Umgebung haben, nachdem das Adobe-Team einen Vorgang zur Bereinigung des Datenraums abgeschlossen hat, oder wenn Sie den `saas:resync`-Befehl mit der Option [—dry-run](https://experienceleague.adobe.com/de/docs/commerce/saas-data-export/data-export-cli-commands#--dry-run) ausführen. Die Verwendung der Option `--cleanup-feed` in anderen Fällen kann zu Datenverlust und Problemen mit der Datensynchronisation führen.

## Verwandtes Lesen

* [Onboarding Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/onboarding-overview.html?lang=de) in unserer Benutzerdokumentation
* [Überprüfen Sie Protokolle und Fehlerbehebung bei Adobe Commerce SaaS-Datenexporten und -](https://experienceleague.adobe.com/de/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging) im Adobe Commerce SaaS-Datenexporthandbuch
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
