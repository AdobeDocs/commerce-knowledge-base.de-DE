---
title: Allgemeine Hilfe zur Fehlerbehebung bei benutzerdefinierten Modulen
description: In diesem Artikel werden allgemeine Tools vorgestellt, die bei der Fehlerbehebung bei benutzerdefinierten Modulen in Adobe Commerce helfen.
exl-id: c6603a2b-dc98-4022-ab29-c081c2b07415
feature: Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Allgemeine Hilfe zur Fehlerbehebung bei benutzerdefinierten Modulen

In diesem Artikel werden allgemeine Tools vorgestellt, die bei der Fehlerbehebung bei benutzerdefinierten Modulen in Adobe Commerce helfen.

## Problem

Wenn Sie feststellen, dass es ein Problem mit den Funktionen Ihres benutzerdefinierten Moduls gibt und Sie keine offensichtlichen Fehlermeldungen erhalten, die das Problem angeben, sollten Sie die Protokolle Ihrer Instanz lesen.

## Lösung

Überprüfen Sie die Protokolle, um festzustellen, ob im Fehler Einträge mit dem Namen des benutzerdefinierten Moduls vorhanden sind.  Je nach den involvierten Fehlern kann die Lösung selbst vorhanden sein. Möglicherweise müssen Sie auch Ihre hilfreichen Adobe Commerce-Protokollinformationen angeben, wenn Sie ein [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) öffnen möchten. In den folgenden Absätzen finden Sie Informationen zum Speicherort der Protokolle und zu möglichen Lösungen.

### Adobe Commerce (alle Bereitstellungsmethoden), Magento Open Source, alle 2.X-Versionen

1. Protokollspeicherorte:
   * [Adobe Commerce in der Cloud-Infrastruktur-Starter-Planarchitektur protokolliert ](/help/how-to/general/log-locations-directories-for-starter-plan.md) in unserer Support-Wissensdatenbank.
   * [Adobe Commerce in der Cloud Infrastructure Pro-Planarchitektur protokolliert ](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) in unserer Support-Wissensdatenbank.
1. Je nach den gefundenen Fehlern werden in diesen Artikeln die folgenden Aktionen beschrieben, wenn Sie ein benutzerdefiniertes Modul aktivieren, deaktivieren oder deinstallieren möchten:
   * [Aktivieren oder deaktivieren Sie Module](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/manage-modules) in unserer Entwicklerdokumentation.
   * [Deinstallieren Sie die Module](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules) in unserer Entwicklerdokumentation.

### Adobe Commerce in der Cloud-Infrastruktur, alle Versionen

1. Speicherorte für Protokolle: [Adobe Commerce in Cloud-Infrastrukturprotokollen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations) in unserer Entwicklerdokumentation.
1. Je nach den Fehlern, die Sie finden, wenn Sie ein benutzerdefiniertes Modul aktivieren, deaktivieren oder deinstallieren möchten, werden in diesen Artikeln in unserer Entwicklerdokumentation diese Aktionen beschrieben:
   * [Installieren, Verwalten und Aktualisieren von Erweiterungen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions).
   * [Fehler bei der Komponentenbereitstellung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/recover-failed-deployment).

## Verwandtes Lesen

In unserer Entwicklerdokumentation:

* [Modulübersicht](https://developer.adobe.com/commerce/php/architecture/modules/overview/)
* [Fehler beim Installieren optionaler Beispieldaten](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/errors-installing-optional-sample-data)
* [Ausnahmebehandlung](https://developer.adobe.com/commerce/webapi/graphql/develop/exceptions/)
* [Ausnahmen während der Installation](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/exceptions-during-installation)
* [Ausführen des Modul-Managers](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/prerequisites)
* [Modulkonfigurationsdateien](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/module-files)
* [Fehler wegen zu wenig Arbeitsspeicher](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade)
