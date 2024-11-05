---
title: Ändern der Inkrement-ID für eine DB-Entität (Bestellung, Rechnung, Kreditkarte usw.) in einem bestimmten Store
description: In diesem Artikel wird beschrieben, wie Sie die Inkrement-ID für eine Adobe Commerce-Datenbank-Entität (DB) (Bestellung, Rechnung, Credit Memo usw.) in einem bestimmten Adobe Commerce-Store mithilfe der SQL-Anweisung "ALTER TABLE"ändern.
exl-id: 3704dd97-3639-44dc-9b8b-cf09f0c04e6c
feature: Invoices
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# Ändern der Inkrement-ID für eine DB-Entität (Bestellung, Rechnung, Kreditkarte usw.) in einem bestimmten Store

In diesem Artikel wird beschrieben, wie Sie die Inkrement-ID für eine Adobe Commerce-Datenbank-Entität (DB) (Bestellung, Rechnung, Kreditmemo usw.) in einem bestimmten Adobe Commerce-Store mithilfe der SQL-Anweisung `ALTER TABLE` ändern.

## Betroffene Versionen

* Adobe Commerce vor Ort: 2.x.x
* Adobe Commerce in Cloud-Infrastruktur: 2.x.x
* MySQL: beliebige [unterstützte Version](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements-tech.html#database)

## Wann müssen Sie die Inkrement-ID ändern (Fälle)?

In diesen Fällen müssen Sie möglicherweise die Inkrement-ID für neue DB-Entitäten ändern:

* Nach einer Sicherung auf einer Live-Site
* Einige Bestelldatensätze sind verloren gegangen, aber ihre IDs werden bereits von Payment Gateways (wie PayPal) für Ihr aktuelles Merchant-Konto verwendet. In diesem Fall stoppen die Zahlungswege die Verarbeitung neuer Bestellungen mit denselben IDs und geben den Fehler &quot;Rechnungskennung duplizieren&quot;zurück.

>[!NOTE]
>
>Sie können auch das Problem mit dem Payment Gateway für PayPal beheben, indem Sie mehrere Zahlungen pro Rechnungskennung in PayPal&#39;s Payment Receiving Preferences zulassen. Siehe [PayPal Gateway-Anfrage abgelehnt - Problem mit doppelten Rechnungen](/help/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.md) in unserer Support-Wissensdatenbank.

## Erforderliche Schritte

1. Suchen Sie Stores und Entitäten, für die die neue Inkrement-ID geändert werden soll.
1. [Verbinden Sie](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html) mit Ihrer MySQL-DB. Für Adobe Commerce in der Cloud-Infrastruktur müssen Sie zunächst [SSH in Ihrer Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) eingeben.
1. Überprüfen Sie den aktuellen Wert für auto\_increment für die Entitätssequenztabelle mithilfe der folgenden Abfrage:

```sql
SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
```

### Beispiel

Wenn Sie eine automatische Inkrementierung für eine Bestellung im Speicher mit *ID=1* überprüfen, lautet der Tabellenname:

```sql
'sequence_order_1'
```

Wenn der Wert der Spalte &quot;`auto_increment`&quot;den Wert &quot;*1234*&quot;hat, erhält die nächste Bestellung, die im Speicher mit &quot;*ID=1*&quot;platziert wird, den Wert &quot;*ID \#10001234*&quot;.

### Verwandte Dokumentation

* [Richten Sie eine Remote-MySQL-Datenbankverbindung ein](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html) in unserer Entwicklerdokumentation.

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

Die nächste Bestellung, die im Store mit *ID=1* platziert wird, hat die *ID \#10002000*.

## Zusätzliche empfohlene Schritte in der Produktionsumgebung (Cloud)

Bevor Sie die `ALTER TABLE` -Abfrage in der Produktionsumgebung von Adobe Commerce in der Cloud-Infrastruktur ausführen, empfehlen wir dringend, die folgenden Schritte auszuführen:

* Testen Sie das gesamte Verfahren zum Ändern der Inkrement-ID in Ihrer Staging-Umgebung.
* [Erstellen Sie ](/help/how-to/general/create-database-dump-on-cloud.md) eine DB-Sicherung, um im Falle eines Fehlers Ihre Produktions-DB wiederherzustellen.

## Verwandte Dokumentation

* [Erstellen Sie einen Datenbank-Dump auf Cloud](/help/how-to/general/create-database-dump-on-cloud.md) in unserer Support-Wissensdatenbank
* [SSH in Ihrer Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) in unserer Entwicklerdokumentation
* [Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung
