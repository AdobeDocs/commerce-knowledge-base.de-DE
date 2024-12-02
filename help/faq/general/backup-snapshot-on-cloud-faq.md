---
title: 'Backup (Schnappschuss) in Cloud: FAQ'
description: In diesem Artikel werden die Grundlagen zum Sichern Ihrer Umgebungen mit Momentaufnahmen in Adobe Commerce in der Cloud-Infrastruktur beschrieben.
exl-id: 0077db74-3e7e-4c98-b215-7f6c089f49e8
feature: Cloud, Iaas
source-git-commit: 0958a8923e27c1341f4b536812b26205685b2b81
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# Backup (Schnappschuss) in Cloud: FAQ

In diesem Artikel wird die Sicherung Ihrer Umgebungen mit Momentaufnahmen in Adobe Commerce in der Cloud-Infrastruktur beschrieben.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.4.x
* Architekturpläne: Starter, Pro Legacy, Pro

## Umgebungsmomentan, Pro-Plan

### Staging- und Produktionsumgebungen

* Manuelle Momentaufnahmen sind nicht für Staging- und Produktionsumgebungen in Pro Plan verfügbar.
* Automatische Momentaufnahmen werden **unabhängig vom Live-Status** Ihrer Site erstellt (Momentaufnahmen, die auch für Sites erstellt wurden, die noch nicht gestartet wurden). Automatische Sicherungen sind nicht öffentlich zugänglich, da sie in einem separaten System gespeichert sind. Sie können [ein Adobe Commerce-Supportticket senden](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket), um ein spezielles Backup anzufordern oder um es aus einem bestimmten Backup wiederherzustellen, indem Sie Datum, Uhrzeit und Zeitzone im Ticket angeben. Beachten Sie außerdem, dass die Unterstützung das Rollback oder die Wiederherstellung der Datenbank nicht für Sie ausführt - sie rufen den Schnappschuss ab, aber Sie müssen die Datenbank selbst wiederherstellen.
* Die Sicherungen werden mit den **verschlüsselten Amazon Web Services Elastic Block Store (AWS EBS)-Momentaufnahmen** erstellt.
* Umgebungsmomentaufnahmen beinhalten Ihr gesamtes System (Dateisystem und Datenbank).
* Die Aufbewahrungszeit für automatische Momentaufnahmen **ist anders** und folgt [dem Zeitplan](/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html?lang=en#backup-and-disaster-recovery).

>[!NOTE]
>In der Cloud-Konsole wird immer [!UICONTROL No backup] in Staging- und Produktionsumgebungen angezeigt. Sie können nur Backups aus der Integrationsumgebung aufnehmen. Wählen Sie im Dropdownmenü mit den Auslassungspunkten **[!UICONTROL Backup]** aus.
>![cloud_console_backup.png](assets/cloud_console_backup.png)





### Integrations- (Entwicklungs-)Umgebung

* Ihre [Integrationsumgebung](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) ist **nicht automatisch gesichert**, Sie können jedoch Momentaufnahmen **manuell** erstellen.
* Sie können manuelle Momentaufnahmen für Integrationsumgebungen in Nicht-Live Stores erstellen.
* Möglicherweise haben Sie **mehrere Momentaufnahmen**, die manuell ausgelöst wurden.
* Ein manuell ausgelöster Schnappschuss wird für **7 Tage** gespeichert.

**Verwandte Artikel in unserer Entwicklerdokumentation:**

* [Sicherung und Wiederherstellung nach Katastrophen](/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#backup-and-disaster-recovery)
* [Erstellen eines Schnappschusses](/docs/commerce-cloud-service/user-guide/develop/storage/snapshots.html)

## Umgebungsmomentaufnahme, Startplan

* Alle Umgebungstypen (Integration, Staging, Produktion) **werden nicht automatisch gesichert**, Sie können jedoch Momentaufnahmen manuell erstellen.
* Sie können manuelle Momentaufnahmen **unabhängig vom Live-Status** Ihrer Site erstellen (Momentaufnahmen, die auch für Sites erstellt wurden, die noch nicht gestartet wurden).
* Ein manuell ausgelöster Schnappschuss wird für **7 Tage** gespeichert.

## Wiederherstellen eines Umgebungs-Snapshots

Um einen vorhandenen Snapshot (in der unterstützten Umgebung: Integration, Staging, Produktion im Starter-Plan oder Integration in Pro-Plan) wiederherzustellen, führen Sie die Schritte unter [Backup-Management: Wiederherstellen eines manuellen Backups](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup) im Handbuch zu Commerce on Cloud Infrastructure aus.

## Datenbanksicherung (DB)

Die DB-Sicherung ist Teil eines Cloud-Snapshots:

>>
Ein Schnappschuss ist eine vollständige Sicherung einer Umgebung, die alle persistenten Daten aus allen laufenden Diensten (z. B. **Ihrer MySQL-Datenbank**, Redis usw.) und allen Dateien enthält, die auf den bereitgestellten Volumes gespeichert sind.

>[!NOTE]
>
>Die bereitgestellten Volumes enthalten/beziehen sich nur auf die [beschreibbaren Reittierungen](/docs/commerce-cloud-service/user-guide/configure/app/properties/properties.html?lang=en#mounts) und enthalten nicht alle Ihre /app-Verzeichnisse. Wie bei den anderen Dateien werden sie von [Build- und Bereitstellungsprozess](/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=en#deployment-workflow) erstellt/generiert und Sie müssen auch die verbleibenden Dateien aus Ihrem Git-Repository auschecken.

[Snapshots und Backup-Verwaltung](/docs/commerce-cloud-service/user-guide/develop/storage/snapshots.html) in unserer Entwicklerdokumentation.

Senden Sie für einen DB-Snapshot von Pro Production und Staging nur eine [Support-Anfrage](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket), wenn Sie die DB von einem bestimmten Zeitpunkt an benötigen. Wenn Sie nur eine aktuelle Sicherung Ihrer DB (in einer beliebigen Umgebung) benötigen, lesen Sie den Knowledge Base-Artikel: [Generieren von Datenbank-Dumps in Cloud](/help/how-to/general/create-database-dump-on-cloud.md).
