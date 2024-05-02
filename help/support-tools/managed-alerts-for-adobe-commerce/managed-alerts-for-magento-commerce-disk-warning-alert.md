---
title: "Managed Warnhinweise für Adobe Commerce: Disk Alert"
description: In diesem Artikel finden Sie Schritte zur Fehlerbehebung, wenn Sie einen Warnhinweis für Adobe Commerce in New Relic erhalten. Um dieses Problem zu beheben, sind sofortige Maßnahmen erforderlich. Der Warnhinweis sieht je nach ausgewähltem Benachrichtigungskanal für Warnhinweise ungefähr wie folgt aus.
exl-id: 07b34db1-11ec-4cf2-ae47-cfc067f91383
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: d7dcb23eee8793b6b97717827feb88c09994bd8b
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis für Datenträger

In diesem Artikel finden Sie Schritte zur Fehlerbehebung, wenn Sie einen Warnhinweis für Adobe Commerce in New Relic erhalten. Um dieses Problem zu beheben, sind sofortige Maßnahmen erforderlich. Der Warnhinweis sieht je nach ausgewähltem Benachrichtigungskanal für Warnhinweise ungefähr wie folgt aus.

![Warnung zur Festplattenwarnung](assets/disk-warning-magento-managed.png){width="500"}

## Betroffene Produkte und Versionen

* Adobe Commerce zur Cloud-Infrastruktur, Pro-Plan-Architektur.

## Problem

Sie erhalten einen Warnhinweis in New Relic, wenn Sie sich bei [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) und eine oder mehrere der Alarmschwellen überschritten wurden. Diese Warnhinweise wurden von Adobe entwickelt, um Kunden mithilfe von Einblicken aus dem Support und Engineering einen Standardsatz zu liefern.

<u> **Tu!** </u>

* Beenden Sie alle geplanten Implementierungen, bis dieser Warnhinweis gelöscht ist.
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site vollständig oder gar nicht reagiert. Anweisungen hierzu finden Sie unter [Installationsanleitung > Wartungsmodus aktivieren oder deaktivieren](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in unserer Entwicklerdokumentation. Stellen Sie sicher, dass Sie Ihre IP-Adresse zur Liste der ausgenommenen IP-Adressen hinzufügen, um sicherzustellen, dass Sie weiterhin auf Ihre Website zugreifen können, um die Fehlerbehebung durchzuführen. Eine Anleitung finden Sie unter [Liste der ausgenommenen IP-Adressen beibehalten](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) in unserer Entwicklerdokumentation.

<u> **Nicht!** </u>

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten auf Ihre Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, die zusätzliche Belastungen für CPU oder Festplatte verursachen können.
* Führen Sie alle wichtigen Verwaltungsaufgaben aus (z. B. Commerce-Administrator, Datenimport/-export).
* Löschen Sie den Cache. Ihre Site reagiert möglicherweise nicht mehr (wenn Sie noch keinen Site-Ausfall haben), wenn Sie eine der &quot;Don&#39;t&quot;-Aktionen ausführen, bevor Sie die Ursache des Warnhinweises untersucht und gelöst haben.

## Lösung

Führen Sie die folgenden Schritte aus, um die Ursache zu identifizieren und zu beheben:

1. Überprüfen Sie in New Relic die Festplatten auf die höchste Verwendung. Anweisungen hierzu finden Sie auf der Registerkarte Speicherung in New Relic [Hostseite für die Infrastrukturüberwachung](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/):
   * Wenn in New Relic ein langsamer Anstieg der Festplattenauslastung auftritt, versuchen Sie die folgenden Optionen:
   * Optimierung des Festplattenspeichers durch Anpassung der Speicherzuordnung. Eine Anleitung finden Sie unter [Festplattenspeicher verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) in unserer Entwicklerdokumentation. Möglicherweise müssen Sie auch mehr Speicherplatz anfordern (wenden Sie sich an Ihr Adobe Account Team).
   * Löschen Sie den Speicherplatz für MySQL. Siehe Abschnitt [MySQL-Speicherplatz ist gering](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) für Schritte.
   * Wenn New Relic eine rapide steigende Festplattenauslastung aufweist, kann dies darauf hinweisen, dass ein Problem dazu geführt hat, dass eine Datei in einem Verzeichnis sehr schnell ansteigt. Führen Sie die folgenden Prüfungen durch:
1. Überprüfen Sie den gesamten Festplattenspeicher, um das Problem zu identifizieren, indem Sie den folgenden Befehl in der CLI/Terminal ausführen: `df -h`
1. Nachdem Sie ein Verzeichnis mit unerwartet hoher und erhöhter Festplattenauslastung identifiziert haben, müssen Sie das betroffene Dateisystem überprüfen. Das folgende Beispiel zeigt, wie Sie den Dateiordner überprüfen `pub/media/`. Dies ist das Verzeichnis, das Adobe Commerce zum Speichern von Protokollen und Big Media-Dateien verwendet. Sie sollten diesen Befehl jedoch für jeden Ordner ausführen, der eine unerwartete Festplattenauslastung anzeigt: `du -sch ~/pub/media/*`.

Wenn die Ausgabe aus dem Terminal eine Datei in einem dieser Verzeichnisse zeigt, die die Festplattenauslastung rapide ansteigt und Sie wissen, dass der Dateiinhalt nicht benötigt wird, sollten Sie die Datei entfernen. Wenn Sie diese Aktion nicht bequem ausführen, [Senden eines Adobe Commerce-Support-Tickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
