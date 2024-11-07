---
title: Upgrade von MariaDB 10.0 auf 10.2 für Adobe Commerce auf Cloud
description: MariaDB 10.0 und 10.1 sind End-of-Life (EOL). [Die Unterstützung endete am 31. März 2019 bzw. am 17. Oktober 2020](https://endoflife.date/mariadb). In diesem Artikel wird erläutert, wie Sie MariaDB von 10.0 auf 10.2, 10.2 auf 10.3 oder 10.4 aktualisieren können, um Adobe Commerce in der Cloud-Infrastruktur zu verwenden.
exl-id: bf66798b-f05c-482f-a2b4-b9bef92b0bab
feature: Best Practices, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# Upgrade von MariaDB 10.0 auf 10.2 für Adobe Commerce auf Cloud

MariaDB 10.0 und 10.1 sind End-of-Life (EOL). [Die Unterstützung endete am 31. März 2019 bzw. am 17. Oktober 2020](https://endoflife.date/mariadb). In diesem Artikel wird erläutert, wie Sie MariaDB von 10.0 auf 10.2, 10.2 auf 10.3 oder 10.4 aktualisieren können, um Adobe Commerce in der Cloud-Infrastruktur zu verwenden.

>[!NOTE]
>
>MariaDB 10.0 ist das Ende der Lebensdauer (End of Life, EOL) und wird in aktuellen Adobe Commerce-Versionen nicht unterstützt. Es empfiehlt sich, eine EOL-Version innerhalb von 30 Tagen nach ihrer Einstellung zu entfernen.

## Betroffene Produkte und Versionen

* MariaDB 10.2 wird für Adobe Commerce in der Cloud-Infrastruktur 2.3.x empfohlen.
* MariaDB 10.4 wird für 2.4.x empfohlen. MariaDB 10.3 ist auch mit Adobe Commerce in der Cloud-Infrastruktur 2.4.x kompatibel.

## Aktualisierungsschritte

Führen Sie die folgenden Schritte aus, um von MariaDB 10.0 auf 10.2 oder 10.2 auf 10.3 oder 10.4 zu aktualisieren:

1. Erstellen Sie eine [DB-Sicherung mithilfe der DB-Sicherungsbefehle von ECE-Tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots). Dies muss vor den Schritten 2 und 3 erfolgen, falls beim Aktualisieren von Tabellen/Zeilen etwas schief geht.
1. [Überprüfen und Konvertieren aller kompakten Tabellen in dynamische Tabellen](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html). Dies ist erforderlich, um potenzielle Datenverluste während der Datenbankaktualisierung zu vermeiden.
1. Suchen Sie nach MYISAM-Tabellen. Sie müssen [alle MyISAM-Tabellen in InnoD](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) konvertieren.
1. Nachdem Sie die Datenbanktabellen und -zeilen vorbereitet haben (die beiden vorherigen Schritte), erstellen Sie eine [DB-Sicherung mithilfe der DB-Sicherungsbefehle für ECE-Tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
1. [Öffnen Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um das Upgrade von MariaDB 10.0 auf 10.2 oder 10.2 auf 10.3 oder 10.4 zu planen. Im Ticket werden Datum und Uhrzeit der Aktualisierung der DB aufgeführt. Das Supportteam benötigt eine 48-stündige Benachrichtigung und das Entwicklungsteam der Händler muss verfügbar sein. Sobald Zeit und Datum für das Upgrade vereinbart sind, führen Sie die folgenden Schritte aus:
   1. Versetzen Sie Ihre Site in den Wartungsmodus und beenden Sie alle DB-Aktivitäten, z. B. Crons.
   1. Erstellen Sie eine [DB-Sicherung mithilfe der DB-Sicherungsbefehle von ECE-Tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
   1. Teilen Sie dem Support mit, dass Sie das Backup abgeschlossen haben. Führen Sie dies über Ihr Support-Ticket aus. Anweisungen zum Anzeigen und Tracking Ihrer Tickets finden Sie im [Benutzerhandbuch des Adobe Commerce Help Center: Tracken Ihrer Tickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) in unserer Support-Wissensdatenbank.
   1. Das Adobe Commerce-Supportteam beginnt mit dem Upgrade-Prozess für MariaDB. Wenn alle oben genannten Schritte ausgeführt wurden und die Datenbank eine durchschnittliche Größe aufweist, kann dies in etwa einer Stunde erfolgen. Größere DBs werden länger dauern. Sobald das Upgrade abgeschlossen ist, werden Sie über Ihr Ticket informiert.
1. Wartungsmodus deaktivieren. Weitere Informationen finden Sie unter [Wartungsmodus aktivieren oder deaktivieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in unserer Entwicklerdokumentation.

## Verwandte Informationen

Weitere Informationen zu den Anforderungen für Adobe Commerce 2.4.x finden Sie unter [Systemanforderungen für Adobe Commerce 2.4 > Datenbank](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements#database) in unserer Entwicklerdokumentation.
