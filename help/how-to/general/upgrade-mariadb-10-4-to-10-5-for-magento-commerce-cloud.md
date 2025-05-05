---
title: Upgrade von MariaDB 10.4 auf 10.5 für Adobe Commerce on Cloud Service
description: MariaDB 10.4 erreicht am 18. Juni 2024 das Ende der Unterstützung. In diesem Artikel wird erläutert, wie Sie MariaDB von 10.4 auf 10.5 aktualisieren können, um Adobe Commerce weiterhin in der Cloud-Infrastruktur zu verwenden.
feature: Best Practices, Cloud
exl-id: 065840b8-28c1-4686-95fc-df3e73152845
source-git-commit: 11f2fae3264a61413c5da1b93ef4980151a1df1e
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Upgrade von MariaDB 10.4 auf 10.5 für Adobe Commerce on Cloud Service

MariaDB ist eine Open-Source-Unternehmensdatenbank, die mit Adobe Commerce verwendet wird.

Das Ende der Unterstützung für MariaDB 10.4 wurde am [. Juni 2024 ](https://endoflife.date/mariadb). Wenn Sie eine nicht unterstützte Version von MariaDB verwenden, sind Sie nicht mehr PCI-kompatibel. In diesem Artikel wird erläutert, wie Sie von MariaDB 10.4 auf 10.5 aktualisieren können, um Adobe Commerce weiterhin in der Cloud-Infrastruktur zu verwenden.

>[!NOTE]
>
>Da MariaDB 10.4 das Ende der Lebensdauer (End of Life, EOL) erreicht, wird es in aktuellen Adobe Commerce-Versionen nicht mehr unterstützt. Es empfiehlt sich, eine EOL-Version innerhalb von 30 Tagen nach ihrem Ende zu deaktivieren.

## Betroffene Produkte und Versionen

* Alle Adobe Commerce On-Premises- und Cloud-Infrastrukturen 2.4.4 und 2.4.5

## Lösung

Nehmen Sie die neuen, nur für die Sicherheit geeigneten Patches (2.4.4-p9 oder 2.4.5-p8) an, die am 11. Juni 2024 veröffentlicht werden, um die Kompatibilität mit MariaDB 10.5 sicherzustellen. Gehen Sie dann wie folgt vor, um von MariaDB 10.4 auf 10.5 zu aktualisieren.

### Upgrade-Schritte für Cloud-Bereitstellungen

1. Erstellen Sie ein [DB-Backup mit ECE-Tools DB-Backup-Befehlen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/storage/snapshots). Diese Sicherung muss vor den Schritten 2 und 3 durchgeführt werden, falls beim Aktualisieren von Tabellen/Zeilen ein Fehler auftritt.
1. [Überprüfen und konvertieren Sie alle kompakten Tabellen in dynamische Tabellen](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/maintenance/mariadb-upgrade). Dieser Schritt ist erforderlich, um einen möglichen Datenverlust während des Datenbank-Upgrades zu vermeiden.
1. Auf MYISAM-Tabellen prüfen. Sie müssen [alle MyISAM-Tabellen in InnoD konvertieren](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud).
1. Nachdem Sie die Datenbanktabellen und -zeilen vorbereitet haben (die beiden vorherigen Schritte), erstellen Sie ein [DB-Backup mit ECE-Tools DB-Backup-Befehlen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
1. [Öffnen Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um das Upgrade von MariaDB 10.4 auf 10.5 zu planen. Geben Sie im Ticket das Datum und die Uhrzeit an, zu der Sie die DB aktualisieren möchten. Das Support-Team benötigt 48 Stunden Vorankündigung, und das Entwicklungsteam des Händlers muss verfügbar sein. Nachdem Zeit und Datum für das Upgrade vereinbart wurden, führen Sie folgende Schritte aus:
   1. Setzen Sie Ihre Site in den Wartungsmodus und stoppen Sie alle DB-Aktivitäten, z. B. Crons.
   1. Erstellen Sie ein [DB-Backup mit ECE-Tools DB-Backup-Befehlen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
   1. Teilen Sie dem Support mit, dass Sie die Sicherung über Ihr Support-Ticket abgeschlossen haben. Anweisungen zum Anzeigen und Verfolgen Ihrer Tickets finden Sie im [Benutzerhandbuch für das Adobe Commerce Help Center: Verfolgen Sie Ihre Tickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) in unserer Support-Wissensdatenbank.
   1. Das Adobe Commerce-Supportteam beginnt dann mit dem MariaDB-Upgrade-Prozess. Wenn alle oben genannten Schritte ausgeführt wurden und die Datenbank eine durchschnittliche Größe aufweist, dauert der Vorgang etwa eine Stunde. Größere DBs dauern länger. Sobald das Upgrade abgeschlossen ist, werden Sie über Ihr Ticket informiert.
1. Deaktivieren Sie den Wartungsmodus. Siehe [Aktivieren oder Deaktivieren des Wartungsmodus](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in unserer Entwicklerdokumentation.

>[!NOTE]
>
>Es wird empfohlen, vor und nach jedem Upgrade-Schritt ein DB-Backup zu erstellen, um mögliche Datenverluste zu vermeiden. Auf diese Weise können Sie zu einem beliebigen Zeitpunkt während des Versions-Upgrades zu einem vorherigen Schritt zurückkehren.

## Verwandtes Lesen

* [Handbuch mit Best Practices für DB](https://experienceleague.adobe.com/de/docs/commerce-operations/upgrade-guide/prepare/prerequisites)Upgrades) für lokale Bereitstellungen.
* [Upgrade von MariaDB 10.0 auf 10.2 für Adobe Commerce on ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10-0-to-10-2-for-magento-commerce-cloud) in unserer Support-Wissensdatenbank.
* [Adobe Commerce-Lebenszyklusrichtlinie](https://experienceleague.adobe.com/de/docs/commerce-operations/release/planning/lifecycle-policy) in unserer Entwicklerdokumentation.
