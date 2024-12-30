---
title: 'Verwaltete Warnhinweise für Adobe Commerce: Kritischer Warnhinweis auf Festplatte'
description: Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie in New Relic einen Warnhinweis zu kritischen Datenträgern für Adobe Commerce erhalten. Sofortiges Handeln ist erforderlich, um das Problem zu beheben. Je nach ausgewähltem Benachrichtigungskanal für Warnhinweise sieht der Warnhinweis etwa wie folgt aus.
exl-id: 03e5694b-7689-4fbf-8781-636fa46ca0d3
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---

# Verwaltete Warnhinweise für Adobe Commerce: Kritischer Warnhinweis auf Festplatte

Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie in New Relic einen Warnhinweis zu kritischen Datenträgern für Adobe Commerce erhalten. Sofortiges Handeln ist erforderlich, um das Problem zu beheben. Je nach ausgewähltem Benachrichtigungskanal für Warnhinweise sieht der Warnhinweis etwa wie folgt aus.

![Kritischer Warnhinweis auf Festplatte](assets/disk-critical-magento-managed.png){width="500"}

## Betroffene Produkte und Versionen

Adobe Commerce-Cloud-Infrastruktur auf Pro-Planarchitektur

## Problem

Sie erhalten einen Warnhinweis in New Relic, wenn Sie sich bei [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) angemeldet haben und einer oder mehrere der Warnhinweisschwellen überschritten wurden. Diese Warnhinweise wurden von Adobe entwickelt, um Kunden mithilfe von Einblicken aus Support und Engineering einen Standardsatz zu bieten.

<u> **DO!** </u>

* Bricht jede geplante Bereitstellung ab, bis dieser Warnhinweis gelöscht wird.
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site nicht mehr reagiert oder überhaupt nicht mehr reagiert. Anweisungen hierzu finden Sie [Installationshandbuch > Wartungsmodus aktivieren oder deaktivieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) . Fügen Sie Ihre IP-Adresse der Liste der von der Steuer befreiten IP-Adressen hinzu, um sicherzustellen, dass Sie weiterhin zur Fehlerbehebung auf Ihre Website zugreifen können. Anweisungen hierzu finden Sie unter [Liste der ausgenommenen IP-Adressen verwalten](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt).

**Tu&#39;s nicht!**

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten auf Ihre Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, was zu zusätzlichen Belastungen für CPU oder die Festplatte führen kann.
* Führen Sie alle wichtigen administrativen Aufgaben aus (z. B. Commerce-Admin, Datenimporte/-exporte).
* Leeren Sie den Cache.

Ihre Site kann nicht mehr reagieren (wenn Sie noch keinen Ausfall der Site feststellen), wenn Sie eine der „Nicht reagieren“-Aktionen durchführen, bevor Sie die Ursache des Warnhinweises untersucht und behoben haben.

## Lösung

Führen Sie diese Schritte aus, um die Ursache zu identifizieren und zu beheben.

>[!WARNING]
>
>Da es sich um einen kritischen Warnhinweis handelt, wird dringend empfohlen, **Schritt 1** auszuführen, bevor Sie versuchen, das Problem zu beheben (Schritt 2 ab).

1. Überprüfen, ob ein Adobe Commerce-Support-Ticket vorhanden ist. Anweisungen hierzu finden Sie unter [Support-Tickets nachverfolgen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) in unserer Support-Wissensdatenbank. Möglicherweise hat der Support eine New Relic-Schwellenwertwarnung erhalten, ein Ticket erstellt und die Arbeit an diesem Problem aufgenommen. Wenn kein Ticket vorhanden ist, erstellen Sie eines. Das Ticket sollte die folgenden Informationen enthalten:
   * Kontaktgrund: Wählen Sie „KRITISCHER New Relic-Warnhinweis empfangen“.
   * Beschreibung des Warnhinweises
   * [New Relic-Vorfall-Link](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Dies ist in Ihren [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) enthalten.
1. Überprüfen Sie in New Relic die Festplatten auf ihre höchste Verwendung. Anweisungen hierzu befinden sich auf der Registerkarte „Speicher“ auf der Seite [ New Relic (Überwachung der Hosts der Infrastruktur:](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage)
   * Wenn in New Relic eine langsamere Zunahme der Speichernutzung festzustellen ist, versuchen Sie die folgenden Optionen:
   * Optimierung des Festplattenspeichers durch Anpassung der Speicherplatzzuweisung Anweisungen hierzu finden Sie unter [Verwalten von Speicherplatz](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) in unserer Entwicklerdokumentation. Möglicherweise benötigen Sie auch mehr Speicherplatz (wenden Sie sich an Ihr Adobe-Account-Team).
   * Löschen Sie Speicherplatz für MySQL. Anweisungen hierzu finden [ in unserer Support](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md)Wissensdatenbank unter „MySQL-Speicherplatz ist niedrig“.
   * Wenn New Relic eine schnell steigende Festplattenauslastung aufweist, kann dies auf ein Problem hinweisen, das dazu geführt hat, dass eine Datei in einem Verzeichnis sehr schnell angestiegen ist. Führen Sie die folgenden Prüfungen durch:
1. Überprüfen Sie den gesamten Speicherplatz, um das Problem zu identifizieren, indem Sie den folgenden Befehl in der CLI/Terminal ausführen: `df -h`
1. Nachdem Sie ein Verzeichnis mit unerwartet großer und zunehmender Festplattenauslastung identifiziert haben, müssen Sie das betroffene Dateisystem überprüfen. Das folgende Beispiel zeigt, wie die `pub/media/` des Dateiverzeichnisses überprüft wird. Dies ist der Ordner, den Commerce zum Speichern von Protokollen und großen Mediendateien verwendet. Sie sollten diesen Befehl jedoch für jedes Verzeichnis ausführen, das eine unerwartete Festplattenauslastung zeigt: `du -sch ~/pub/media/*`

Wenn die Ausgabe vom Terminal zeigt, dass eine Datei in einem dieser Verzeichnisse schnell ansteigt und Sie wissen, dass der Inhalt der Datei nicht benötigt wird, sollten Sie die Datei entfernen. Wenn Sie mit dieser Aktion nicht vertraut sind, [ Sie ein Adobe Commerce-Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
