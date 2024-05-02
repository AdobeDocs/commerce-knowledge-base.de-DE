---
title: Variable für die Datenbankinkrementierung auto_inkrement auf "3"Adobe Commerce in unserer Cloud Pro-Architektur eingestellt
description: Dies ist das erwartete Verhalten von Adobe Commerce bei Cloud Infrastructure Pro-Planarchitekturlösungen aufgrund der 3-Knoten-Architektur und kann nicht geändert werden.
exl-id: ea478cbc-2dc2-41c9-8ea7-7e2f308e5948
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Variable für die Datenbankinkrementierung auto_inkrement auf &quot;3&quot;Adobe Commerce in unserer Cloud Pro-Architektur eingestellt

Dies ist das erwartete Verhalten von Adobe Commerce bei Cloud Infrastructure Pro-Planarchitekturlösungen aufgrund der 3-Knoten-Architektur und kann nicht geändert werden.

Der Galera-Datenbankcluster wird verwendet. Hierbei handelt es sich um einen Datenbankcluster mit einer MariaDB MySQL-Datenbank pro Knoten mit einer automatischen Inkrementierungseinstellung von drei für eindeutige IDs in jeder Datenbank.

<u>Warum wird die in Pro-Clustern verwendete Inkrement-ID nicht immer durch 3 getrennt/inkrementiert?</u>

Die Inkrement-ID, die in Clustern verwendet wird, wird aufgrund der Funktionsweise von Galera nicht immer durch 3 getrennt/inkrementiert.

Jeder der drei Server verwaltet seinen eigenen ID-Speicherplatz. Die verwendete Inkrementierung hängt davon ab, welcher MySQL-Haupt-Datenbankserver (je nach relativer Belastung) verwendet wird - also welche Lücken variieren.
Wenn Sie SSH zu jedem Knoten verwenden und eine Verbindung zur lokalen MySQL-Instanz herstellen, die auf diesem Knoten ausgeführt wird, indem Sie Port 3307 verwenden (anstatt mit dem &quot;main&quot;auf dem Standardport 3306 bereitgestellt zu werden), sehen Sie die folgende Abbildung:

![auto_inkrement](assets/auto_increment_id.png)

Wenn beispielsweise der gewählte Haupt node 1 ist, wobei `auto_increment_offset = 1`, würde die ID um 1 inkrementiert. Wenn dann zu einem späteren Zeitpunkt ein neuer Hauptknoten ausgewählt wird, z. B. Knoten 3, wobei `auto_increment_offset = 3`, würde sie stattdessen um 3 erhöht werden.

## Nützliche Links

Siehe in unserer Entwicklerdokumentation:

* [Cloud für Adobe Commerce > Pro-Architektur > Backup und Disaster Recovery](https://devdocs.magento.com/cloud/architecture/pro-architecture.html#backup-and-disaster-recovery)
* [Cloud für Adobe Commerce > Installationsvoraussetzungen: Datenbank](https://devdocs.magento.com/cloud/before/before-workspace-magento-prereqs.html#database)
