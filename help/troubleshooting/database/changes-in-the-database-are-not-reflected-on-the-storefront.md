---
title: Änderungen an der Datenbank werden nicht in der Storefront übernommen
description: Dieser Artikel enthält Lösungen, mit denen Verzögerungen oder Unterbrechungen bei der Anwendung von Entitätenaktualisierungen vermieden werden können. Trigger Dazu gehört auch, wie verhindert werden kann, dass Änderungsprotokolltabellen übergroß werden, und wie Tabellen- [!DNL MySQL]  eingerichtet werden.
exl-id: ac52c808-299f-4d08-902f-f87db1fa7ca6
feature: Catalog Management, Categories, Services, Storefront
role: Developer
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# Änderungen an der Datenbank werden nicht in der Storefront übernommen

Dieser Artikel enthält Lösungen, mit denen Verzögerungen oder Unterbrechungen bei der Anwendung von Entitätenaktualisierungen vermieden werden können. Dazu gehört auch, wie verhindert werden kann, dass Änderungsprotokolltabellen übergroß werden, und wie [!DNL MySQL] Tabellen-Trigger eingerichtet werden.

Betroffene Produkte und Versionen:

* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x
* Adobe Commerce On-Premises 2.2.x, 2.3.x

## Problem

Änderungen, die Sie an der Datenbank vornehmen, werden nicht in die Storefront übernommen, oder es kommt zu einer erheblichen Verzögerung bei der Anwendung von Entitätenaktualisierungen. Zu den möglicherweise betroffenen Entitäten gehören Produkte, Kategorien, Preise, Inventar, Katalogregeln, Verkaufsregeln und Zielgruppenregeln.

## Ursache

Wenn Ihre Indexer [für eine Aktualisierung nach Zeitplan konfiguriert sind](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers) kann das Problem durch eine oder mehrere Tabellen mit zu großen Änderungsprotokollen oder nicht eingerichteten MySQL-Triggern verursacht werden.

### Übergroße Änderungsprotokolltabellen

Die Änderungsprotokolltabellen werden so groß, wenn der `indexer_update_all_views` Cron-Vorgang nicht mehrmals erfolgreich abgeschlossen wurde.

Änderungsprotokolltabellen sind die Datenbanktabellen, in denen die Änderungen an Entitäten verfolgt werden. Ein Datensatz wird in einer Änderungsprotokolltabelle gespeichert, solange die Änderung nicht angewendet wird. Dies wird vom `indexer_update_all_views` Cron-Auftrag ausgeführt. Eine Adobe Commerce-Datenbank enthält mehrere Änderungsprotokolltabellen. Sie werden nach dem folgenden Muster benannt: INDEXER\_TABLE\_NAME + &#39;\_cl&#39;, z. B. `catalog_category_product_cl`, `catalog_product_category_cl`. Weitere Informationen zum Tracking von Änderungen in der Datenbank finden Sie im Artikel [Indizierungsübersicht > Mview](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) in unserer Entwicklerdokumentation.

### [!DNL MySQL] Datenbank-Trigger nicht eingerichtet

Es besteht der Verdacht, dass keine Datenbank-Trigger eingerichtet werden, wenn nach dem Hinzufügen oder Ändern einer Entität (Produkt, Kategorie, Zielregel usw.) keine Datensätze zur entsprechenden Änderungsprotokolltabelle hinzugefügt werden.

## Lösung

>[!WARNING]
>
>Es wird dringend empfohlen, ein Datenbank-Backup zu erstellen, bevor Sie Manipulationen durchführen, und diese in Zeiten hoher Site-Auslastung zu vermeiden.

### Vermeidung von Übergrößen von Änderungsprotokolltabellen

Stellen Sie sicher, dass der `indexer_update_all_views` Cron-Auftrag immer erfolgreich abgeschlossen wird.

Sie können die folgende SQL-Abfrage verwenden, um alle fehlgeschlagenen Instanzen des `indexer_update_all_views` Cron-Auftrags abzurufen:

```sql
select * from cron_schedule where job_code = "indexer_update_all_views" and status
  <> "success" and status <> "pending";
```

Alternativ können Sie den Status in den Protokollen überprüfen, indem Sie nach den `indexer_update_all_views` Einträgen suchen:

* `<install_directory>/var/log/cron.log` - für Versionen 2.3.1+ und 2.2.8+
* `<install_directory>/var/log/system.log` - für frühere Versionen

### Trigger [!DNL MySQL] Tabelle zurücksetzen

Um die fehlenden [!DNL MySQL]-Trigger einzurichten, müssen Sie den Indexermodus neu einstellen:

1. Wechseln Sie zu „Beim Speichern“.
1. Zurück zu „Planmäßig“ wechseln.

Verwenden Sie den folgenden Befehl, um diesen Vorgang auszuführen.

>[!WARNING]
>
>Bevor Sie den Indexermodus wechseln, empfehlen wir, Ihre Website in den [&#128279;](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html?lang=de#maintenance-mode)-Modus zu versetzen und [Cron-Aufträge zu deaktivieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=de#disable-cron-jobs) um Datenbanksperren zu vermeiden.

```bash
php bin/magento indexer:set-mode {realtime|schedule} [indexerName]
```

>[!INFO]
>
>Die Indexer-bezogenen Datenbank-Trigger werden hinzugefügt, wenn der Indexermodus auf „Zeitplan“ festgelegt ist, und entfernt, wenn der Indexermodus auf „Echtzeit“ festgelegt ist. Wenn die Trigger in Ihrer Datenbank fehlen, während die Indexer auf Zeitplan eingestellt sind, ändern Sie die Indexer in Echtzeit und ändern Sie sie dann wieder zurück in Zeitplan. Dadurch werden die Trigger zurückgesetzt.

## Verwandtes Lesen

* [[!DNL MySQL] Tabellen sind zu groß](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26945) in unserer Support-Wissensdatenbank
* [Indizierung: [!DNL Mview]](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) in unserer Entwicklerdokumentation
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
