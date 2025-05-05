---
title: Upgrade von MariaDB 10.0 auf 10.2 für Adobe Commerce on Cloud Service
description: MariaDB 10.0 und 10.1 sind Ende der Lebensdauer (End of Life, EOL). [Die Unterstützung endete am 31. März 2019 bzw. am 17. Oktober 2020](https://endoflife.date/mariadb). In diesem Artikel wird erläutert, wie MariaDB von 10.0 auf 10.2 oder 10.2 auf 10.3 oder auf 10.4 aktualisiert werden kann, um Adobe Commerce auf Cloud-Infrastrukturen zu verwenden.
exl-id: bf66798b-f05c-482f-a2b4-b9bef92b0bab
feature: Best Practices, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# Upgrade von MariaDB 10.0 auf 10.2 für Adobe Commerce on Cloud Service

MariaDB 10.0 und 10.1 sind Ende der Lebensdauer (End of Life, EOL). [Der Support endete am 31. März 2019 bzw. am 17. Oktober 2020](https://endoflife.date/mariadb). In diesem Artikel wird erläutert, wie MariaDB von 10.0 auf 10.2 oder 10.2 auf 10.3 oder auf 10.4 aktualisiert werden kann, um Adobe Commerce auf Cloud-Infrastrukturen zu verwenden.

>[!NOTE]
>
>MariaDB 10.0 wurde eingestellt und wird in aktuellen Adobe Commerce-Versionen nicht unterstützt. Es empfiehlt sich, eine EOL-Version innerhalb von 30 Tagen nach ihrem Ende zu deaktivieren.

## Betroffene Produkte und Versionen

* MariaDB 10.2 wird für Adobe Commerce auf Cloud-Infrastruktur 2.3.x empfohlen.
* MariaDB 10.4 wird für 2.4.x empfohlen. MariaDB 10.3 ist auch mit Adobe Commerce on Cloud Infrastructure 2.4.x kompatibel.

## Upgrade-Schritte

Führen Sie die folgenden Schritte aus, um von MariaDB 10.0 auf 10.2 oder 10.2 auf 10.3 oder auf 10.4 zu aktualisieren:

1. Erstellen Sie ein [DB-Backup mit ECE-Tools DB-Backup-Befehlen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/storage/snapshots). Dies muss vor den Schritten 2 und 3 erfolgen, falls beim Aktualisieren von Tabellen/Zeilen ein Fehler auftritt.
1. [Überprüfen und konvertieren Sie alle kompakten Tabellen in dynamische Tabellen](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html?lang=de). Dies ist erforderlich, um einen möglichen Datenverlust während des Datenbank-Upgrades zu vermeiden.
1. Auf MYISAM-Tabellen prüfen. Sie müssen [alle MyISAM-Tabellen in InnoD konvertieren](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=de).
1. Nachdem Sie die Datenbanktabellen und -zeilen vorbereitet haben (die beiden vorherigen Schritte), erstellen Sie ein [DB-Backup mit ECE-Tools DB-Backup-Befehlen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
1. [Öffnen Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um das Upgrade von MariaDB 10.0 auf 10.2 oder 10.2 auf 10.3 oder 10.4 zu planen. Geben Sie im Ticket Datum und Uhrzeit an, zu der Sie die DB aktualisieren möchten. Das Supportteam benötigt 48 Stunden Vorankündigung und das Merchants-Entwicklungsteam muss verfügbar sein. Nachdem Zeit und Datum für das Upgrade vereinbart wurden, führen Sie folgende Schritte aus:
   1. Setzen Sie Ihre Site in den Wartungsmodus und stoppen Sie alle DB-Aktivitäten, z. B. Crons.
   1. Erstellen Sie ein [DB-Backup mit ECE-Tools DB-Backup-Befehlen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
   1. Teilen Sie dem Support mit, dass Sie die Sicherung abgeschlossen haben. Verwenden Sie dazu Ihr Support-Ticket. Anweisungen zum Anzeigen und Verfolgen Ihrer Tickets finden Sie im [Benutzerhandbuch für das Adobe Commerce Help Center: Verfolgen Sie Ihre Tickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) in unserer Support-Wissensdatenbank.
   1. Das Adobe Commerce-Supportteam beginnt mit dem MariaDB-Upgrade-Prozess. Wenn alle oben genannten Schritte ausgeführt wurden und die Datenbank eine durchschnittliche Größe aufweist, kann dies in etwa einer Stunde geschehen. Größere DBs benötigen mehr Zeit. Sobald die Aktualisierung abgeschlossen ist, werden Sie über Ihr Ticket informiert.
1. Deaktivieren Sie den Wartungsmodus. Siehe [Aktivieren oder Deaktivieren des Wartungsmodus](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu den Anforderungen für Adobe Commerce 2.4.x finden Sie unter [Systemanforderungen für Adobe Commerce 2.4 > Datenbank](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/system-requirements#database) in unserer Entwicklerdokumentation.
