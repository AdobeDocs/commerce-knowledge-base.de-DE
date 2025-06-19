---
title: Ändern der Inkrement-ID für eine DB-Entität (Bestellung, Rechnung, Gutschrift usw.) in einem bestimmten Geschäft
description: In diesem Artikel wird beschrieben, wie Sie die Inkrement-ID für eine Adobe Commerce-Datenbankentität (DB) (Bestellung, Rechnung, Gutschrift usw.) in einem bestimmten Adobe Commerce Store mithilfe der SQL-Anweisung „ALTER TABLE“ ändern können.
exl-id: 3704dd97-3639-44dc-9b8b-cf09f0c04e6c
feature: Invoices
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# Ändern der Inkrement-ID für eine DB-Entität (Bestellung, Rechnung, Gutschrift usw.) in einem bestimmten Geschäft

In diesem Artikel wird beschrieben, wie Sie die Inkrement-ID für eine Adobe Commerce-Datenbankentität (DB) (Bestellung, Rechnung, Gutschrift usw.) in einem bestimmten Adobe Commerce Store mithilfe der `ALTER TABLE` SQL-Anweisung ändern.

## Betroffene Versionen

* Adobe Commerce On-Premise: 2.x.x
* Adobe Commerce auf Cloud-Infrastruktur: 2.x.x
* MySQL: Beliebige [unterstützte Version](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/system-requirements)

## Wann müssten Sie die Inkrement-ID (Fälle) ändern?

Möglicherweise müssen Sie in folgenden Fällen die Inkrement-ID für neue DB-Entitäten ändern:

* Nach einer Hard Backup-Wiederherstellung auf einer Live Site
* Einige Auftragsdatensätze sind verloren gegangen, aber ihre IDs werden bereits von Zahlungs-Gateways (wie PayPal) für Ihr aktuelles Händlerkonto verwendet. In diesem Fall verarbeiten die Zahlungs-Gateways keine neuen Bestellungen mehr, die dieselben IDs haben, sondern geben den Fehler „Rechnungsduplikat-ID“ zurück

>[!NOTE]
>
>Sie können das Problem mit dem Zahlungs-Gateway für PayPal auch beheben, indem Sie in den Zahlungseingangsvoreinstellungen von PayPal mehrere Zahlungen pro Rechnungs-ID zulassen. Siehe [PayPal Gateway Rejected Request - Duplicate Invoice Issue](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26838) in unserer Support-Wissensdatenbank.

## Vorausgesetzte Schritte

1. Suchen Sie nach Stores und Entitäten, für die die neue Inkrement-ID geändert werden soll.
1. [Verbinden](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql-remote) mit Ihrer MySQL-DB. Für Adobe Commerce in der Cloud-Infrastruktur müssen Sie zunächst [SSH in Ihre Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=de).
1. Überprüfen Sie den aktuellen auto\_increment-Wert für die Entitätssequenztabelle mithilfe der folgenden Abfrage:

```sql
SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
```

### Beispiel

Wenn Sie eine automatische Inkrementierung für eine Bestellung im Store mit *ID=1* überprüfen, würde der Tabellenname wie folgt lauten:

```sql
'sequence_order_1'
```

Wenn der Wert der `auto_increment` Spalte *1234* ist, hat die nächste Bestellung im Speicher mit *ID=1* die *ID \#100001234*.

### Verwandte Dokumentation

* [Einrichten einer Remote-MySQL-Datenbankverbindung](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql-remote) in unserer Entwicklerdokumentation.

## Entität aktualisieren, um Inkrement-ID zu ändern

Aktualisieren Sie die Entität mithilfe der folgenden Abfrage:

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!WARNING]
>
>Wichtig: Der neue Inkrementwert muss größer als der aktuelle Wert sein, nicht kleiner!

### Beispiel

Nach dem Ausführen der folgenden Abfrage:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

Die nächste Bestellung im Store mit *ID=1* hat die *ID \#100002000*.

## Weitere empfohlene Schritte für die Produktionsumgebung (Cloud)

Bevor Sie die `ALTER TABLE` Abfrage in der Produktionsumgebung von Adobe Commerce in der Cloud-Infrastruktur ausführen, empfehlen wir dringend die folgenden Schritte:

* Testen des gesamten Verfahrens zur Änderung der Inkrement-ID in der Staging-Umgebung
* [Erstellen](/help/how-to/general/create-database-dump-on-cloud.md) Sie ein DB-Backup, um die Produktions-DB bei einem Fehler wiederherzustellen.

## Verwandte Dokumentation

* [Erstellen eines Datenbank-Dump in der Cloud](/help/how-to/general/create-database-dump-on-cloud.md) in unserer Support-Wissensdatenbank
* [SSH in Ihre Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=de) in unserer Entwicklerdokumentation
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
