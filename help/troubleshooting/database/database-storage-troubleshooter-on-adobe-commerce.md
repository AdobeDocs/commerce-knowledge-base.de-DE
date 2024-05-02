---
title: Fehlerbehebung bei der Datenbankspeicherung in Adobe Commerce
description: Dieser Artikel ist ein Tool zur Fehlerbehebung für Kunden in Adobe Commerce, die Probleme mit Datenbanken haben. Klicken Sie auf jede Frage, um die Antwort in jedem Schritt der Problembehebung anzuzeigen. Abhängig von Ihren Symptomen und Ihrer Konfiguration wird in der Fehlerbehebung erläutert, wie Sie Probleme mit Speicherplatz und Konfiguration in Datenbanken beheben können.
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 0%

---

# Fehlerbehebung bei der Datenbankspeicherung in Adobe Commerce

Dieser Artikel ist ein Tool zur Fehlerbehebung für Kunden in Adobe Commerce, die Probleme mit Datenbanken haben. Klicken Sie auf jede Frage, um die Antwort in jedem Schritt der Problembehebung anzuzeigen. Abhängig von Ihren Symptomen und Ihrer Konfiguration wird in der Fehlerbehebung erläutert, wie Sie Probleme mit Speicherplatz und Konfiguration in Datenbanken beheben können.

## Schritt 1: Verzeichnis mit Leerzeichen identifizieren {#step-1}

+++**Haben Sie eine `/tmp` Problem durch fehlenden Speicherplatz?**

Dies kann an einer Reihe von Symptomen wie dem `/tmp` Einbinden, da sie voll, Site-Down oder nicht in der Lage sind, SSH in einem Knoten zu platzieren. Möglicherweise treten auch Fehler wie _Auf dem Gerät verbleibender Speicherplatz (28)_. Für eine Liste der Fehler, die durch `/tmp` vollständig, Überprüfung [/tmp-Bereitstellung voll](/help/troubleshooting/miscellaneous/tmp-mount-full.md).

Oder haben Sie eine `/data/mysql` Problem durch fehlenden Speicherplatz? Dies lässt sich auch an einer Vielzahl von Symptomen erkennen, darunter Site-Ausfall, Kunden, die nicht in der Lage sind, Produkte zum Warenkorb hinzuzufügen, Verbindungsfehler zur Datenbank und Galeria-Fehler wie _SQLSTATE\[08S01\]: Kommunikationslink-Fehler: 1047 WSREP_. Eine Liste der Fehler, die durch geringen MySQL-Speicherplatz verursacht werden, finden Sie unter [MySQL-Speicherplatz in Adobe Commerce in der Cloud-Infrastruktur ist gering](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md).

Wenn Sie sich nicht sicher sind, ob Sie ein Problem mit dem Festplattenspeicher haben und ein New Relic-Konto haben, gehen Sie zu [New Relic Infrastructure Monitoring Hosts-Seite](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/). Klicken Sie dort auf die **Speicherung** ändern Sie die **Diagrammanzeigen** von 5 auf 20 Ergebnisse herabsetzen und in der Tabelle auf hohe Festplattenauslastung in der Grafik oder Tabelle Disc Used % nachsehen. Detaillierte Anweisungen finden Sie unter [New Relic Infrastructure Monitoring > Registerkarte &quot;Storage&quot;]https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage).

Wenn eines der oben beschriebenen Symptome bei Ihnen auftritt, überprüfen Sie den Status Ihrer Inoden, um sicherzustellen, dass dies nicht durch Probleme mit der Dateinummer verursacht wird. Führen Sie dazu den folgenden Befehl im CLI/Terminal aus:\
`df -ih`

Ist IUse% > 90%?

a. YES - Dies wird durch zu viele Dateien verursacht. Überprüfen Sie die Schritte zum sicheren Entfernen von Dateien unter [Sicheres Löschen von Dateien ohne Speicherplatz, Adobe Commerce in der Cloud-Infrastruktur](/help/troubleshooting/miscellaneous/safely-delete-files-when-out-of-disk-space-adobe-commerce-on-our-cloud-architecture.md). Fahren Sie mit [Schritt 2](#step-2) nachdem Sie diese Schritte ausgeführt haben. Wenn Sie mehr Speicherplatz anfordern möchten, [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Prüfung der Leerzeichen. Ausführen `df -h | grep mysql` und dann `df -h | grep tmp` im CLI/Terminal, um die Festplattenspeicherplatznutzung im `/tmp` und `/data/mysql` Verzeichnissen. Fahren Sie mit [Schritt 3](#step-3).

+++

## Schritt 2: Überprüfen des Festplattenspeichers {#step-2}

+++**Überprüfen Sie die Festplattenspeicherplatznutzung?**

Nachdem Sie die Anzahl der Dateien reduziert haben, führen Sie `df -h | grep mysql` und dann `df -h | grep tmp` im CLI/Terminal, um die Festplattenspeicherplatznutzung in zu überprüfen. `/tmp` und `/data/mysql`. Ist größer als 70%, verwendet für `/tmp` oder `/data/mysql`?

a. JA - fahren Sie mit [Schritt 3](#step-3).
b. NO - Abfragen können die verfügbare Datenspeicherung erschöpfen. Dadurch kann der Knoten abstürzen, die Abfrage wird beendet und die `tmp` -Dateien. Untersuchen Sie die Ausgabe der `SHOW PROCESSLIST;` in der MySQL-CLI für Abfragen, die die Ursache des Problems sein können. [Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um mehr Speicherplatz anzufordern.

+++

## Schritt 3: Verzeichnis mit hoher Auslastung identifizieren {#step-3}

+++**Welches Verzeichnis hat mehr als 70% verwendet?**

Welches Verzeichnis hat mehr als 70% verwendet? `/tmp` oder `/data/mysql`?

>[!NOTE]
>
>Standardmäßig schreibt tmpdir in die Datenbank `/tmp`. Um zu überprüfen, ob Ihre Datenbankkonfiguration noch auf diesem Standard basiert, führen Sie den folgenden Befehl in MySQL CLI aus: `SHOW VARIABLES LIKE "TMPDIR";` Wenn der Datenbank-TMPdir noch schreibt in `/tmp`angezeigt wird, wird `/tmp` in der Spalte Wert .

a. `/tmp` - Fahren Sie fort mit [Schritt 4](#step-4). \
b. `/data/mysql` - Fahren Sie fort mit [Schritt 5](#step-5).

+++

## Schritt 4: Fehlerbehebung bei der vollständigen Bereitstellung von /tmp {#step-4}

+++**Fehlerbehebung für die vollständige Bereitstellung von /tmp**

[Fehlerbehebung für die vollständige Bereitstellung von /tmp für Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md), scrollen Sie nach unten und probieren Sie die Lösungen und Best Practices aus. Dann ausführen `df -h | grep mysql` und dann `df -h | grep tmp` im CLI/Terminal, um die Festplattenspeicherplatznutzung in zu überprüfen. `/tmp` und `/data/mysql` Verzeichnisse\
  &lt; 70 % verwendet?

>[!NOTE]
>
>Die Lösungen in [Fehlerbehebung für die vollständige Bereitstellung von /tmp für Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) wurden für Händler entwickelt, die die Variablen für Datenbank-TMPdir nicht geändert haben, die standardmäßig in `/tmp`. Wenn Sie den tmpdir-Wert geändert haben, finden Sie die Anweisungen unter [Fehlerbehebung für die vollständige Bereitstellung von /tmp für Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) wird nicht helfen.

a. JA - Sie haben das Problem gelöst. \
b. NO - [Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um mehr Speicherplatz anzufordern.

+++

## Schritt 5: Standardeinstellung überprüfen {#step-5}

+++**Standardeinstellung aktivieren**

Ihre Datenbankkonfiguration befindet sich möglicherweise nicht mehr in der ursprünglichen Standardeinstellung. Suchen Sie die Konfiguration des Datenbank-TMPdir , indem Sie sie in der MySQL-CLI ausführen: `SELECT @@DATADIR;`. Wenn `/data/mysql/` ausgegeben wird, schreibt der Datenbank-TMPdir jetzt in `/data/mysql/`. Versuchen Sie, den Speicherplatz in diesem Verzeichnis zu erhöhen, indem Sie die Schritte unter [MySQL-Speicherplatz auf Adobe Commerce in unserer Cloud-Infrastruktur ist gering](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md). Dann ausführen `df -h | grep mysql` und dann `df -h | grep tmp` im CLI/Terminal, um die Festplattenspeicherplatznutzung in zu überprüfen. `/data/mysql` und `/tmp`.\
  &lt; 70 % verwendet?

a. JA - Sie haben das Problem gelöst. \
b. NO - [Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um mehr Speicherplatz anzufordern.

+++

[Zurück zu Schritt 1](#step-1)
