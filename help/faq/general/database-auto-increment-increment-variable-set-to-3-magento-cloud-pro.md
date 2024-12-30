---
title: Datenbank automatisch inkrementieren Variable auf „3“ gesetzt Adobe Commerce in unserer Cloud Pro-Architektur
description: Dies ist das erwartete Verhalten für Adobe Commerce bei Cloud-Infrastruktur-Pro-Plan-Architekturlösungen aufgrund der 3-Knoten-Architektur und kann nicht geändert werden.
exl-id: ea478cbc-2dc2-41c9-8ea7-7e2f308e5948
feature: Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Datenbank automatisch inkrementieren Variable auf „3“ gesetzt Adobe Commerce in unserer Cloud Pro-Architektur

Dies ist das erwartete Verhalten für Adobe Commerce bei Cloud-Infrastruktur-Pro-Plan-Architekturlösungen aufgrund der 3-Knoten-Architektur und kann nicht geändert werden.

Es wird der Galera-Datenbankcluster verwendet, bei dem es sich um einen Datenbankcluster mit einer MariaDB MySQL-Datenbank pro Knoten und einer automatischen Inkrementierungseinstellung von drei für eindeutige IDs in jeder Datenbank handelt.

<u>Warum wird die auf Pro-Clustern verwendete Inkrement-ID nicht immer um 3 getrennt/inkrementiert?</u>

Die für Cluster verwendete Inkrement-ID wird aufgrund der Funktionsweise von Galera nicht immer um 3 getrennt/inkrementiert.

Jeder der drei Server verwaltet seinen eigenen ID-Speicherplatz, und das verwendete Inkrement hängt davon ab, welcher der MySQL-Hauptdatenbankserver ist (je nach relativer Last) - daher die unterschiedlichen Lücken.
Wenn Sie SSH auf jedem Knoten installieren und eine Verbindung zur lokalen MySQL-Instanz herstellen, die auf diesem Knoten ausgeführt wird, indem Sie Port 3307 verwenden (anstatt zum „Haupt“ auf dem Standard-Port 3306 weitergeleitet zu werden), sehen Sie die folgende Abbildung:

![auto_increment](assets/auto_increment_id.png)

Wenn das ausgewählte Hauptmenü beispielsweise Knoten 1 mit `auto_increment_offset = 1` ist, wird die ID um 1 erhöht. Wenn dann ein neuer Hauptknoten zu einem späteren Zeitpunkt ausgewählt wird, z. B. Knoten 3, bei dem `auto_increment_offset = 3` ist, wird er stattdessen um 3 erhöht.

## Nützliche Links

Siehe in unserer Entwicklerdokumentation:

* [Cloud für Adobe Commerce > Pro-Architektur > Sicherung und Notfallwiederherstellung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#backup-and-disaster-recovery)
* [Cloud für Adobe Commerce > Installationsvoraussetzungen: Datenbank](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview)
