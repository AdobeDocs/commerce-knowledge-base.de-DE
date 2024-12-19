---
title: 'Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis bezüglich Festplatte'
description: Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie einen Warnmeldungsdatenträger für Adobe Commerce in New Relic erhalten. Sofortiges Handeln ist erforderlich, um das Problem zu beheben. Je nach ausgewähltem Benachrichtigungskanal für Warnhinweise sieht der Warnhinweis etwa wie folgt aus.
exl-id: 07b34db1-11ec-4cf2-ae47-cfc067f91383
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis bezüglich Festplatte

Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie einen Warnmeldungsdatenträger für Adobe Commerce in New Relic erhalten. Sofortiges Handeln ist erforderlich, um das Problem zu beheben. Je nach ausgewähltem Benachrichtigungskanal für Warnhinweise sieht der Warnhinweis etwa wie folgt aus.

![Warnhinweis bezüglich Festplatte](assets/disk-warning-magento-managed.png){width="500"}

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, Pro-Planarchitektur.

## Problem

Sie erhalten einen Warnhinweis in New Relic, wenn Sie sich bei [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) angemeldet haben und einer oder mehrere der Warnhinweisschwellen überschritten wurden. Diese Warnhinweise wurden von Adobe entwickelt, um Kunden mithilfe von Einblicken aus Support und Engineering einen Standardsatz zu bieten.

<u> **DO!** </u>

* Bricht jede geplante Bereitstellung ab, bis dieser Warnhinweis gelöscht wird.
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site nicht mehr reagiert oder überhaupt nicht mehr reagiert. Anweisungen hierzu finden Sie [Installationshandbuch > Wartungsmodus aktivieren oder deaktivieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in unserer Entwicklerdokumentation. Fügen Sie Ihre IP-Adresse der Liste der von der Steuer befreiten IP-Adressen hinzu, um sicherzustellen, dass Sie weiterhin zur Fehlerbehebung auf Ihre Website zugreifen können. Anweisungen hierzu finden Sie unter [Liste der ausgenommenen IP-Adressen verwalten](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt) in unserer Entwicklerdokumentation.

<u> **Nicht!** </u>

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten auf Ihre Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, was zu zusätzlichen Belastungen für CPU oder die Festplatte führen kann.
* Führen Sie alle wichtigen administrativen Aufgaben aus (z. B. Commerce-Admin, Datenimporte/-exporte).
* Leeren Sie den Cache. Ihre Site kann nicht mehr reagieren (wenn Sie noch keinen Ausfall der Site feststellen), wenn Sie eine der „Nicht reagieren“-Aktionen durchführen, bevor Sie die Ursache des Warnhinweises untersucht und behoben haben.

## Lösung

Führen Sie die folgenden Schritte aus, um die Ursache zu identifizieren und zu beheben:

1. Überprüfen Sie in New Relic die Festplatten auf ihre höchste Verwendung. New Relic Anweisungen hierzu befinden sich auf der Registerkarte „Speicher“ auf der [ „Hosts für die Infrastrukturüberwachung“](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/):
   * Wenn in New Relic eine langsamere Zunahme der Speichernutzung festzustellen ist, versuchen Sie die folgenden Optionen:
   * Optimierung des Festplattenspeichers durch Anpassung der Speicherplatzzuweisung Anweisungen hierzu finden Sie unter [Verwalten von Speicherplatz](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) in unserer Entwicklerdokumentation. Möglicherweise benötigen Sie auch mehr Speicherplatz (wenden Sie sich an Ihr Adobe-Account-Team).
   * Löschen Sie Speicherplatz für MySQL. Anweisungen finden [ unter „MySQL](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md)Speicherplatz ist niedrig“.
   * Wenn New Relic eine schnell steigende Festplattenauslastung aufweist, kann dies auf ein Problem hinweisen, das dazu geführt hat, dass eine Datei in einem Verzeichnis sehr schnell angestiegen ist. Führen Sie die folgenden Prüfungen durch:
1. Überprüfen Sie den gesamten Speicherplatz, um das Problem zu identifizieren, indem Sie den folgenden Befehl in der CLI/Terminal ausführen: `df -h`
1. Nachdem Sie ein Verzeichnis mit unerwartet großer und zunehmender Festplattenauslastung identifiziert haben, müssen Sie das betroffene Dateisystem überprüfen. Das folgende Beispiel zeigt, wie die `pub/media/` des Dateiverzeichnisses überprüft wird. Dies ist der Ordner, den Adobe Commerce zum Speichern von Protokollen und großen Mediendateien verwendet. Sie sollten diesen Befehl jedoch für jedes Verzeichnis ausführen, das eine unerwartete Festplattenauslastung aufweist: `du -sch ~/pub/media/*`.

Wenn die Ausgabe vom Terminal zeigt, dass eine Datei in einem dieser Verzeichnisse schnell ansteigt und Sie wissen, dass der Inhalt der Datei nicht benötigt wird, sollten Sie die Datei entfernen. Wenn Sie mit dieser Aktion nicht vertraut sind, [ Sie ein Adobe Commerce-Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
