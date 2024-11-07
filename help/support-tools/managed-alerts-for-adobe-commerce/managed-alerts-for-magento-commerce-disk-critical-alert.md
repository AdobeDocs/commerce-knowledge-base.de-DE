---
title: "Managed Warnhinweise für Adobe Commerce: Disk-critical alert"
description: In diesem Artikel finden Sie Schritte zur Fehlerbehebung, wenn Sie einen kritischen Datenträgerwarnungen für Adobe Commerce in New Relic erhalten. Um dieses Problem zu beheben, sind sofortige Maßnahmen erforderlich. Der Warnhinweis sieht je nach ausgewähltem Benachrichtigungskanal für Warnhinweise ungefähr wie folgt aus.
exl-id: 03e5694b-7689-4fbf-8781-636fa46ca0d3
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---

# Verwaltete Warnhinweise für Adobe Commerce: Warnungen bezüglich der Festplatte

In diesem Artikel finden Sie Schritte zur Fehlerbehebung, wenn Sie einen kritischen Datenträgerwarnungen für Adobe Commerce in New Relic erhalten. Um dieses Problem zu beheben, sind sofortige Maßnahmen erforderlich. Der Warnhinweis sieht je nach ausgewähltem Benachrichtigungskanal für Warnhinweise ungefähr wie folgt aus.

![kritische Warnung bezüglich der Festplatte](assets/disk-critical-magento-managed.png){width="500"}

## Betroffene Produkte und Versionen

Adobe Commerce-Cloud-Infrastruktur für Pro-Plan-Architektur

## Problem

Sie erhalten eine Warnung in New Relic, wenn Sie bis zu [Warnhinweise für Adobe Commerce verwalten](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) angemeldet haben und mindestens eine der Warnschwellen überschritten wurde. Diese Warnhinweise wurden von Adobe entwickelt, um Kunden mithilfe von Einblicken aus dem Support und Engineering einen Standardsatz zu liefern.

<u> **Do!** </u>

* Beenden Sie alle geplanten Implementierungen, bis dieser Warnhinweis gelöscht ist.
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site vollständig oder gar nicht reagiert. Anweisungen finden Sie unter [Installationshandbuch > Wartungsmodus aktivieren oder deaktivieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) . Stellen Sie sicher, dass Sie Ihre IP-Adresse zur Liste der ausgenommenen IP-Adressen hinzufügen, um sicherzustellen, dass Sie weiterhin auf Ihre Website zugreifen können, um die Fehlerbehebung durchzuführen. Anweisungen hierzu finden Sie unter [Verwalten der Liste der ausgenommenen IP-Adressen](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt).

**Nicht!**

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten zu Ihrer Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, die zusätzliche Belastungen für CPU oder Festplatte verursachen können.
* Führen Sie alle wichtigen Verwaltungsaufgaben aus (z. B. Commerce-Administrator, Datenimport/-export).
* Löschen Sie den Cache.

Ihre Site reagiert möglicherweise nicht mehr (wenn Sie noch keinen Site-Ausfall haben), wenn Sie eine der &quot;Don&#39;t&quot;-Aktionen ausführen, bevor Sie die Ursache des Warnhinweises untersucht und gelöst haben.

## Lösung

Führen Sie diese Schritte aus, um die Ursache zu identifizieren und zu beheben.

>[!WARNING]
>
>Da dies ein kritischer Warnhinweis ist, wird dringend empfohlen, **Schritt 1** auszuführen, bevor Sie versuchen, das Problem zu beheben (ab Schritt 2).

1. Überprüfen Sie, ob ein Adobe Commerce-Support-Ticket vorhanden ist. Anweisungen finden Sie unter [Tracken Ihrer Support-Tickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) in unserer Support-Wissensdatenbank. Der Support hat möglicherweise einen New Relic-Schwellenwert-Warnhinweis erhalten, ein Ticket erstellt und mit der Bearbeitung des Problems begonnen. Wenn kein Ticket existiert, erstellen Sie eines. Das Ticket sollte die folgenden Informationen enthalten:
   * Kontaktgrund: Wählen Sie &quot;New Relic CRITICAL alert&quot;.
   * Beschreibung der Warnung.
   * [New Relic-Vorfall-Link](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Dies ist in Ihren [verwalteten Warnhinweisen für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) enthalten.
1. Überprüfen Sie in New Relic die Festplatten auf die höchste Verwendung. Anweisungen finden Sie auf der Registerkarte Speicherung auf der Seite mit den New Relic [Überwachungshosts für die Infrastruktur:](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage)
   * Wenn in New Relic ein langsamer Anstieg der Festplattenauslastung auftritt, versuchen Sie die folgenden Optionen:
   * Optimierung des Festplattenspeichers durch Anpassung der Speicherzuordnung. Anweisungen finden Sie unter [Festplattenspeicher verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) in unserer Entwicklerdokumentation. Möglicherweise müssen Sie auch mehr Speicherplatz anfordern (wenden Sie sich an Ihr Adobe Account Team).
   * Löschen Sie den Speicherplatz für MySQL. Informationen zu den Schritten finden Sie unter [MySQL-Speicherplatz ist gering](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) in unserer Support-Wissensdatenbank.
   * Wenn New Relic eine rapide steigende Festplattenauslastung aufweist, kann dies darauf hinweisen, dass ein Problem dazu geführt hat, dass eine Datei in einem Verzeichnis sehr schnell ansteigt. Führen Sie die folgenden Prüfungen durch:
1. Überprüfen Sie den gesamten Festplattenspeicher, um das Problem zu identifizieren, indem Sie den folgenden Befehl in der CLI/Terminal ausführen: `df -h`
1. Nachdem Sie ein Verzeichnis mit unerwartet hoher und erhöhter Festplattenauslastung identifiziert haben, müssen Sie das betroffene Dateisystem überprüfen. Das folgende Beispiel zeigt, wie Sie das Dateiverzeichnis `pub/media/` überprüfen. Dies ist das Verzeichnis, das Commerce zum Speichern von Protokollen und Big Media-Dateien verwendet. Sie sollten diesen Befehl jedoch für jeden Ordner ausführen, der eine unerwartete Festplattenauslastung anzeigt: `du -sch ~/pub/media/*`

Wenn die Ausgabe aus dem Terminal eine Datei in einem dieser Verzeichnisse zeigt, die die Festplattenauslastung rapide ansteigt und Sie wissen, dass der Dateiinhalt nicht benötigt wird, sollten Sie die Datei entfernen. Wenn Sie diese Aktion nicht ausführen möchten, senden Sie ein Adobe Commerce-Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).[
