---
title: 'Backup (Snapshot) in der Cloud: Häufig gestellte Fragen'
description: In diesem Artikel werden die Grundlagen zum Sichern Ihrer Umgebungen mit Snapshots auf Adobe Commerce in der Cloud-Infrastruktur behandelt.
exl-id: 0077db74-3e7e-4c98-b215-7f6c089f49e8
feature: Cloud, Iaas
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 0%

---

# Backup (Snapshot) in der Cloud: Häufig gestellte Fragen

Dieser Artikel behandelt das Sichern Ihrer Umgebungen mit Momentaufnahmen der Adobe Commerce auf Cloud-Infrastrukturen.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.4.x
* Architekturpläne: Starter, Pro Legacy, Pro

## Umgebungs-Snapshot, Pro-Plan

### Staging- und Produktionsumgebungen

* Manuelle Momentaufnahmen sind für Staging- und Produktionsumgebungen in Pro Plan nicht verfügbar.
* Automatische Momentaufnahmen werden erstellt **unabhängig vom Live-Status** Ihrer Site (Momentaufnahmen werden auch für Sites erstellt, die noch nicht gestartet wurden). Automatische Sicherungen sind nicht öffentlich zugänglich, da sie in einem separaten System gespeichert sind.
Sie können [ein Adobe Commerce-Support-Ticket ](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket), um eine spezielle Sicherung anzufordern oder eine Wiederherstellung aus einer bestimmten Sicherung durchzuführen, wobei Sie Datum, Uhrzeit und Zeitzone im Ticket angeben. Nachdem das Infrastruktur-Team den Schnappschuss bereitgestellt hat, führen Sie den folgenden Befehl an der Stelle aus, an der der Schnappschuss platziert wurde, um den Zeitstempel zu ermitteln, an dem er ursprünglich erstellt wurde:

  `cat /mnt/recovery/vol-<volume_id>/snap.time`

  Beispielausgabe:

  <strong>2025-01-13 08:42:17.123000+00:00</strong>


* Der Support generiert bei Bedarf keine manuellen Momentaufnahmen. Beachten Sie außerdem, dass die -Unterstützung nicht das Rollback oder die Wiederherstellung der Datenbank für Sie durchführt - sie rufen den Snapshot ab, aber Sie müssen die Datenbank selbst wiederherstellen.
* Automatische Momentaufnahmen werden erstellt **unabhängig vom Live-Status** Ihrer Site (Momentaufnahmen werden auch für Sites erstellt, die noch nicht gestartet wurden). Automatische Sicherungen werden in einem separaten System gespeichert und sind für die Öffentlichkeit nicht zugänglich.
Sie können [ein Adobe Commerce-Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md), um eine spezielle Sicherung anzufordern oder eine Wiederherstellung aus einer bestimmten Sicherung durchzuführen, wobei Sie Datum, Uhrzeit und Zeitzone im Ticket angeben. Der Support generiert bei Bedarf keine manuellen Momentaufnahmen.
Beachten Sie außerdem, dass die -Unterstützung nicht das Rollback oder die Wiederherstellung der Datenbank für Sie durchführt - sie rufen den Snapshot ab, aber Sie müssen die Datenbank selbst wiederherstellen.
* Die Backups werden mithilfe der **verschlüsselten Momentaufnahmen des Amazon Web Services Elastic Block Store (AWS EBS))**.
* Umgebungs-Snapshots umfassen Ihr gesamtes System (Dateisystem und Datenbank).
* Die Aufbewahrungsdauer für automatische Momentaufnahmen **ist unterschiedlich** und folgt [dem Zeitplan](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/architecture/pro-architecture#backup-and-disaster-recovery).

>[!NOTE]
>
>Die Cloud-Konsole zeigt [!UICONTROL No backup] immer in Staging- und Produktionsumgebungen an. Es können nur Sicherungen aus der Integrationsumgebung durchgeführt werden. Wählen Sie **[!UICONTROL Backup]** im Dropdown-Menü mit den Auslassungspunkten aus.
>
>![cloud_console_backup.png](assets/cloud_console_backup.png)

### Integrations-(Entwicklungs-)Umgebung

* Ihre [Integrationsumgebung](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-27242) wird **nicht automatisch gesichert** Sie können jedoch Momentaufnahmen (**)**.
* Sie können manuelle Momentaufnahmen für Integrationsumgebungen in Nicht-Live-Stores erstellen.
* Möglicherweise **mehrere Momentaufnahmen** die manuell ausgelöst wurden.
* Ein manuell ausgelöster Snapshot wird **7 Tage** gespeichert.

**Verwandte Artikel in unserer Entwicklerdokumentation:**

* [Sicherung und Notfallwiederherstellung](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/architecture/pro-architecture#backup-and-disaster-recovery)
* [Snapshot erstellen](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/storage/snapshots)

## Umgebungs-Snapshot, Starterplan

* Alle Umgebungstypen (Integration, Staging, Produktion) **werden nicht automatisch gesichert** Sie können Snapshots jedoch manuell erstellen.
* Sie können manuelle Momentaufnahmen **unabhängig vom Live-Status** Ihrer Site erstellen (Momentaufnahmen werden auch für Sites erstellt, die noch nicht gestartet wurden).
* Ein manuell ausgelöster Snapshot wird **7 Tage** gespeichert.

## Wiederherstellen eines Umgebungsschnappschusses

Um einen vorhandenen Snapshot (in der unterstützten Umgebung: Integration, Staging, Produktion im Starterplan oder Integration in Pro Plan) wiederherzustellen, führen Sie die Schritte in [Backup-Verwaltung: Manuelles Backup wiederherstellen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup) in unserem Handbuch zu Commerce in Cloud-Infrastruktur aus.

## Datenbank-Backup (DB)

Die Datenbanksicherung ist Teil eines Cloud-Snapshots:

Ein Snapshot ist ein vollständiges Backup einer Umgebung, das alle persistenten Daten aus allen ausgeführten Services (z. B. **MySQL-Datenbank**, Redis usw.) und allen auf den bereitgestellten Volumes gespeicherten Dateien enthält.

>[!NOTE]
>
>Die bereitgestellten Volumes enthalten/beziehen sich nur auf [beschreibbare Bereitstellungen](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/configure/app/properties/properties#mounts) und enthalten nicht alle Ihre `/app`. Die anderen Dateien werden vom Build- und [-Prozess erstellt/generiert](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/architecture/pro-develop-deploy-workflow#deployment-workflow) und Sie müssen auch die verbleibenden Dateien aus Ihrem Git-Repository auschecken.

[Snapshots und Backup-Verwaltung](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/storage/snapshots) in unserer Entwicklerdokumentation.

Senden Sie eine [Support-Anfrage](/help/help-center-guide/help-center/magento-help-center-user-guide.md) für einen DB-Snapshot von Pro Production and Staging nur, wenn Sie die DB zu einem bestimmten Zeitpunkt benötigen. Wenn Sie nur eine aktuelle Sicherung Ihrer DB benötigen (in einer beliebigen Umgebung), finden Sie weitere Informationen im Knowledge-Base-Artikel [Generieren von Datenbank-Dumps in der Cloud](/help/how-to/general/create-database-dump-on-cloud.md).
