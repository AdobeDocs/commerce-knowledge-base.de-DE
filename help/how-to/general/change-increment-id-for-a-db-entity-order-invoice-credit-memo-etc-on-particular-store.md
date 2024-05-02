---
title: Ändern der Inkrement-ID für eine DB-Entität (Bestellung, Rechnung, Kreditkarte usw.) in einem bestimmten Geschäft
description: In diesem Artikel wird beschrieben, wie Sie die Inkrement-ID für eine Adobe Commerce-Datenbank-Entität (DB) ändern (Bestellung, Rechnung, Kreditmemo usw.) in einem bestimmten Adobe Commerce-Store mithilfe der SQL-Anweisung "ALTER TABLE"ein.
exl-id: 3704dd97-3639-44dc-9b8b-cf09f0c04e6c
feature: Invoices
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Ändern der Inkrement-ID für eine DB-Entität (Bestellung, Rechnung, Kreditkarte usw.) in einem bestimmten Geschäft

In diesem Artikel wird beschrieben, wie Sie die Inkrement-ID für eine Adobe Commerce-Datenbank-Entität (DB) ändern (Bestellung, Rechnung, Kreditmemo usw.) in einem bestimmten Adobe Commerce-Store, der die `ALTER TABLE` SQL-Anweisung.

## Betroffene Versionen

* Adobe Commerce vor Ort: 2.x.x
* Adobe Commerce in Cloud-Infrastruktur: 2.x.x
* MySQL: any [unterstützte Version](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements-tech.html#database)

## Wann müssen Sie die Inkrement-ID ändern (Fälle)?

In diesen Fällen müssen Sie möglicherweise die Inkrement-ID für neue DB-Entitäten ändern:

* Nach einer Sicherung auf einer Live-Site
* Einige Bestelldatensätze sind verloren gegangen, aber ihre IDs werden bereits von Payment Gateways (wie PayPal) für Ihr aktuelles Merchant-Konto verwendet. In diesem Fall stoppen die Zahlungswege die Verarbeitung neuer Bestellungen mit denselben IDs und geben den Fehler &quot;Rechnungskennung duplizieren&quot;zurück.

>[!NOTE]
>
>Sie können auch das Problem mit dem Payment Gateway für PayPal beheben, indem Sie mehrere Zahlungen pro Rechnungskennung in PayPal&#39;s Payment Receiving Preferences zulassen. Siehe [PayPal Gateway Anfrage abgelehnt - Problem mit doppelten Rechnungen](/help/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.md) in unserer Wissensdatenbank.

## Erforderliche Schritte

1. Suchen Sie Stores und Entitäten, für die die neue Inkrement-ID geändert werden soll.
1. [Verbinden](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html) auf Ihre MySQL-DB. Für Adobe Commerce in der Cloud-Infrastruktur müssen Sie zunächst [SSH in Ihrer Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Überprüfen Sie den aktuellen Wert für auto\_increment für die Entitätssequenztabelle mithilfe der folgenden Abfrage:

```sql
SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
```

### Beispiel

Wenn Sie eine automatische Inkrementierung für eine Bestellung im Speicher mit *ID=1* lautet der Tabellenname:

```sql
'sequence_order_1'
```

Wenn der Wert der `auto_increment` column is *1234*, die nächste Bestellung, die im Store mit *ID=1* wird die *ID \#10001234*.

### Verwandte Dokumentation

* [Eine Remote-Verbindung zur MySQL-Datenbank einrichten](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html) in unserer Entwicklerdokumentation.

## Entität aktualisieren, um die Inkrement-ID zu ändern

Aktualisieren Sie die Entität mithilfe der folgenden Abfrage:

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!WARNING]
>
>Wichtig: Der neue Inkrementwert muss größer als der aktuelle sein, nicht kleiner!

### Beispiel

Nach Ausführung der folgenden Abfrage:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

die nächste Bestellung, die im Geschäft mit *ID=1* wird die *ID \#10002000*.

## Zusätzliche empfohlene Schritte in der Produktionsumgebung (Cloud)

Vor der Ausführung des `ALTER TABLE` Abfrage zur Produktionsumgebung von Adobe Commerce in der Cloud-Infrastruktur. Wir empfehlen dringend, die folgenden Schritte auszuführen:

* Testen Sie das gesamte Verfahren zum Ändern der Inkrement-ID in Ihrer Staging-Umgebung.
* [Erstellen](/help/how-to/general/create-database-dump-on-cloud.md) DB-Sicherung zur Wiederherstellung der Produktions-DB im Falle eines Fehlers

## Verwandte Dokumentation

* [Datenbank-Dump in Cloud erstellen](/help/how-to/general/create-database-dump-on-cloud.md) in unserer Wissensdatenbank.
* [SSH in Ihrer Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) in unserer Entwicklerdokumentation.
