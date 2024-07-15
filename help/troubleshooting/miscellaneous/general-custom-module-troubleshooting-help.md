---
title: Allgemeine Hilfe zur Fehlerbehebung bei benutzerdefinierten Modulen
description: In diesem Artikel werden allgemeine Tools vorgestellt, die bei der Fehlerbehebung bei benutzerdefinierten Modulen in Adobe Commerce helfen.
exl-id: c6603a2b-dc98-4022-ab29-c081c2b07415
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
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
   * [Aktivieren oder deaktivieren Sie Module](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-enable.html) in unserer Entwicklerdokumentation.
   * [Deinstallieren Sie die Module](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-uninstall-mods.html) in unserer Entwicklerdokumentation.

### Adobe Commerce in der Cloud-Infrastruktur, alle Versionen

1. Speicherorte für Protokolle: [Adobe Commerce in Cloud-Infrastrukturprotokollen](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html) in unserer Entwicklerdokumentation.
1. Je nach den Fehlern, die Sie finden, wenn Sie ein benutzerdefiniertes Modul aktivieren, deaktivieren oder deinstallieren möchten, werden in diesen Artikeln in unserer Entwicklerdokumentation diese Aktionen beschrieben:
   * [Installieren, Verwalten und Aktualisieren von Erweiterungen](https://devdocs.magento.com/guides/v2.3/cloud/howtos/install-components.html).
   * [Fehler bei der Komponentenbereitstellung](https://devdocs.magento.com/guides/v2.3/cloud/trouble/trouble_comp-deploy-fail.html).

## Verwandtes Lesen

In unserer Entwicklerdokumentation:

* [Modulübersicht](https://devdocs.magento.com/guides/v2.3/architecture/archi_perspectives/components/modules/mod_intro.html)
* [Fehler beim Installieren optionaler Beispieldaten](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/tshoot_sample-data.html)
* [Ausnahmebehandlung](https://devdocs.magento.com/guides/v2.3/graphql/develop/exceptions.html)
* [Ausnahmen während der Installation](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/tshoot_exceptions.html)
* [Ausführen des Modul-Managers](https://devdocs.magento.com/guides/v2.3/comp-mgr/module-man/compman-checklist.html)
* [Modulkonfigurationsdateien](https://devdocs.magento.com/guides/v2.3/config-guide/config/config-files.html)
* [Fehler wegen zu wenig Arbeitsspeicher](https://devdocs.magento.com/guides/v2.3/comp-mgr/trouble/cman/out-of-memory.html)
