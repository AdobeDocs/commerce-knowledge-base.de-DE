---
title: Upgrade von MariaDB 10.4 auf 10.5 für Adobe Commerce auf Cloud
description: MariaDB 10.4 beendet den Support am 18. Juni 2024. In diesem Artikel wird erläutert, wie Sie MariaDB von 10.4 auf 10.5 aktualisieren können, um Adobe Commerce weiterhin in der Cloud-Infrastruktur zu verwenden.
feature: Best Practices, Cloud
source-git-commit: 401a36722b3336b47dd76bb12ace34f0bf55b8e6
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# Upgrade von MariaDB 10.4 auf 10.5 für Adobe Commerce auf Cloud

MariaDB ist eine Open-Source-Unternehmensdatenbank, die mit Adobe Commerce verwendet wird.

MariaDB 10.4 beendet die Unterstützung am [18. Juni 2024](https://endoflife.date/mariadb). Sie sind nicht mehr PCI-kompatibel, wenn Sie eine nicht unterstützte Version von MariaDB verwenden. In diesem Artikel wird beschrieben, wie Sie von MariaDB 10.4 auf 10.5 aktualisieren, um Adobe Commerce weiterhin in der Cloud-Infrastruktur zu verwenden.

>[!NOTE]
>
>Da MariaDB 10.4 das Ende der Lebensdauer (End of Life, EOL) erreicht, wird es in aktuellen Adobe Commerce-Versionen nicht mehr unterstützt. Es empfiehlt sich, eine EOL-Version innerhalb von 30 Tagen nach ihrer Einstellung zu entfernen.

## Betroffene Produkte und Versionen

* Alle Adobe Commerce vor Ort und auf Cloud-Infrastruktur 2.4.4 und 2.4.5

## Lösung

Nehmen Sie die neuen reinen Sicherheits-Patches (2.4.4-p9 oder 2.4.5-p8) an, die am 11. Juni 2024 veröffentlicht werden, um die Kompatibilität mit MariaDB 10.5 sicherzustellen. Gehen Sie dann wie folgt vor, um ein Upgrade von MariaDB 10.4 auf 10.5 durchzuführen.

### Aktualisierungsschritte für Cloud-Bereitstellungen

1. Erstellen Sie eine [DB-Backup mit ECE-Tools DB-Sicherungsbefehlen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots). Diese Sicherung muss vor den Schritten 2 und 3 durchgeführt werden, falls beim Aktualisieren von Tabellen/Zeilen etwas schief geht.
1. [Überprüfen und Konvertieren aller kompakten Tabellen in dynamische Tabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/mariadb-upgrade). Dieser Schritt ist erforderlich, um potenzielle Datenverluste während der Datenbankaktualisierung zu vermeiden.
1. Suchen Sie nach MYISAM-Tabellen. Sie müssen [Konvertieren aller MyISAM-Tabellen in InnoD](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud).
1. Nachdem Sie die Datenbanktabellen und -zeilen vorbereitet haben (die beiden vorherigen Schritte), erstellen Sie eine [DB-Backup mit ECE-Tools DB-Sicherungsbefehlen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
1. [Support-Ticket öffnen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) , um das Upgrade von MariaDB 10.4 auf 10.5 zu planen. Geben Sie im Ticket das Datum und die Uhrzeit an, zu dem die DB aktualisiert werden soll. Das Supportteam benötigt eine 48-stündige Benachrichtigung und das Entwicklungsteam des Händlers muss verfügbar sein. Sobald Zeit und Datum für das Upgrade vereinbart sind, führen Sie die folgenden Schritte aus:
   1. Versetzen Sie Ihre Site in den Wartungsmodus und beenden Sie alle DB-Aktivitäten, z. B. Crons.
   1. Erstellen Sie eine [DB-Backup mit ECE-Tools DB-Sicherungsbefehlen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
   1. Teilen Sie dem Support mit, dass Sie das Backup über Ihr Supportticket abgeschlossen haben. Anweisungen zum Anzeigen und Tracking Ihrer Tickets finden Sie unter [Adobe Commerce Help Center-Benutzerhandbuch: Tickets verfolgen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) in unserer Wissensdatenbank.
   1. Das Adobe Commerce-Supportteam beginnt dann mit dem Upgrade-Prozess für MariaDB. Wenn alle oben genannten Schritte ausgeführt wurden und die Datenbank eine durchschnittliche Größe aufweist, dauert der Prozess etwa eine Stunde. Größere DBs brauchen länger. Sobald das Upgrade abgeschlossen ist, werden Sie über Ihr Ticket informiert.
1. Wartungsmodus deaktivieren. Siehe Abschnitt [Aktivieren oder Deaktivieren des Wartungsmodus](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in unserer Entwicklerdokumentation.

## Verwandte Informationen

* [Handbuch zu Best Practices bei der DB-Aktualisierung](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/prerequisites) für Vor-Ort-Bereitstellungen.
* [Upgrade von MariaDB 10.0 auf 10.2 für Adobe Commerce auf Cloud](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10-0-to-10-2-for-magento-commerce-cloud) in unserer Wissensdatenbank.
* [Adobe Commerce-Lebenszyklusrichtlinie](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy) in unserer Entwicklerdokumentation.
