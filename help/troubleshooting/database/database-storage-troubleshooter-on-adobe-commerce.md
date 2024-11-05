---
title: Fehlerbehebung bei der Datenbankspeicherung in Adobe Commerce
description: Dieser Artikel ist ein Tool zur Fehlerbehebung für Kunden in Adobe Commerce, die Probleme mit Datenbanken haben. Klicken Sie auf jede Frage, um die Antwort in jedem Schritt der Problembehebung anzuzeigen. Abhängig von Ihren Symptomen und Ihrer Konfiguration wird in der Fehlerbehebung erläutert, wie Sie Probleme mit Speicherplatz und Konfiguration in Datenbanken beheben können.
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# Fehlerbehebung bei der Datenbankspeicherung in Adobe Commerce

Dieser Artikel ist ein Tool zur Fehlerbehebung für Kunden in Adobe Commerce, die Probleme mit Datenbanken haben. Klicken Sie auf jede Frage, um die Antwort in jedem Schritt der Problembehebung anzuzeigen. Abhängig von Ihren Symptomen und Ihrer Konfiguration wird in der Fehlerbehebung erläutert, wie Sie Probleme mit Speicherplatz und Konfiguration in Datenbanken beheben können.

## Schritt 1: Verzeichnis mit Leerzeichen identifizieren {#step-1}

+++**Haben Sie ein `/tmp` -Problem, das durch einen Mangel an Platz verursacht wird?**

Dies kann an einer Reihe von Symptomen erkennbar sein, z. B. dass die `/tmp` -Bereinigung voll ist, die Site heruntergefahren ist oder nicht in der Lage ist, SSH in einen Knoten zu setzen. Möglicherweise treten auch Fehler wie _Kein Speicherplatz auf dem Gerät (28)_ auf. Eine Liste der Fehler, die dadurch verursacht werden, dass `/tmp` voll ist, finden Sie unter [/tmp mountet full](/help/troubleshooting/miscellaneous/tmp-mount-full.md) .

Oder haben Sie ein `/data/mysql`-Problem, das durch einen Platzmangel verursacht wird? Dies kann auch an verschiedenen Symptomen erkennbar sein, darunter Site-Ausfall, Kunden, die keine Produkte zum Warenkorb hinzufügen können, Verbindungsfehler zur Datenbank und Galeria-Fehler wie _SQLSTATE\[08S01\]: Kommunikationslink-Fehler: 1047 WSREP_. Eine Liste der Fehler, die durch niedrigen [!DNL MySQL] Speicherplatz verursacht werden, finden Sie unter [[!DNL MySQL] In der Cloud-Infrastruktur ist der Speicherplatz in Adobe Commerce gering](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md).

Wenn Sie sich nicht sicher sind, ob Sie ein Problem mit dem Festplattenspeicher haben und ein New Relic-Konto haben, gehen Sie zur Seite [New Relic Infrastructure monitoring Hosts page](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/). Klicken Sie dann auf die Registerkarte **Speicher**, ändern Sie die Dropdown-Liste **Diagrammanzeigen** von 5 auf 20 Ergebnisse und suchen Sie in der Tabelle nach einer hohen Festplattenauslastung im Diagramm bzw. in der Tabelle &quot;Verwendete Festplatten %&quot;. Weitere Informationen finden Sie unter [New Relic Infrastructure Monitoring > Storage tab]https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage).

Wenn eines der oben beschriebenen Symptome bei Ihnen auftritt, überprüfen Sie den Status Ihrer Inoden, um sicherzustellen, dass dies nicht durch Probleme mit der Dateinummer verursacht wird. Führen Sie dazu den folgenden Befehl im CLI/Terminal aus:\
`df -ih`

Ist IUse% > 90%?

a. YES - Dies wird durch zu viele Dateien verursacht. Überprüfen Sie die Schritte zum sicheren Entfernen von Dateien in [Sicheres Löschen von Dateien, wenn nicht genügend Speicherplatz vorhanden ist, Adobe Commerce in der Cloud-Infrastruktur](/help/troubleshooting/miscellaneous/safely-delete-files-when-out-of-disk-space-adobe-commerce-on-our-cloud-architecture.md). Fahren Sie mit [Schritt 2](#step-2) fort, nachdem Sie diese Schritte ausgeführt haben. Wenn Sie mehr Speicherplatz anfordern möchten, senden Sie [ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Prüfung der Leerzeichen. Führen Sie `df -h | grep mysql` und dann `df -h | grep tmp` im CLI/Terminal aus, um die Festplattenspeicherplatznutzung in den Verzeichnissen `/tmp` und `/data/mysql` zu überprüfen. Fahren Sie mit [Schritt 3](#step-3) fort.

+++

## Schritt 2: Überprüfen des Festplattenspeichers {#step-2}

+++**Überprüfen Sie die Speicherplatznutzung?**

Nachdem Sie die Anzahl der Dateien reduziert haben, führen Sie `df -h | grep mysql` und dann `df -h | grep tmp` in der CLI/Terminal aus, um die Speicherplatznutzung in `/tmp` und `/data/mysql` zu überprüfen. Werden mehr als 70 % für `/tmp` oder `/data/mysql` verwendet?

a. JA - Fahren Sie mit [Schritt 3](#step-3) fort.
b. NO - Abfragen können die verfügbare Datenspeicherung erschöpfen. Dadurch kann der Knoten abstürzen, die Abfrage wird beendet und die `tmp`-Dateien werden entfernt. Untersuchen Sie die Ausgabe von `SHOW PROCESSLIST;` in der [!DNL MySQL]-CLI auf Abfragen, die die Ursache des Problems sein können. [Senden Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um mehr Platz anzufordern.

+++

## Schritt 3: Verzeichnis mit hoher Auslastung identifizieren {#step-3}

+++**Welcher Ordner hat mehr als 70 % verwendet?**

Welches Verzeichnis hat mehr als 70% verwendet? `/tmp` oder `/data/mysql`?

>[!NOTE]
>
>Standardmäßig schreibt TMPdir der Datenbank in `/tmp`. Um zu überprüfen, ob Ihre Datenbankkonfiguration noch auf diesem Standard basiert, führen Sie den folgenden Befehl in [!DNL MySQL] CLI aus: `SHOW VARIABLES LIKE "TMPDIR";` Wenn der Datenbank-TMPdir noch in `/tmp` schreibt, wird in der Spalte &quot;Wert&quot;der Wert angezeigt, `/tmp`.

a. `/tmp` - Fahren Sie mit [Schritt 4](#step-4) fort. \
b. `/data/mysql` - Fahren Sie mit [Schritt 5](#step-5) fort.

+++

## Schritt 4: Fehlerbehebung bei der vollständigen Bereitstellung von /tmp {#step-4}

+++**Fehlerbehebung /tmp-Bereitstellung voll**

[Fehlerbehebung /tmp-Bereitstellung für Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md), scrollen Sie nach unten und probieren Sie die Lösungen und Best Practices aus. Führen Sie dann `df -h | grep mysql` und dann `df -h | grep tmp` in der CLI/Terminal aus, um die Speichernutzung in den Verzeichnissen `/tmp` und `/data/mysql` zu überprüfen.\
  &lt; 70 % verwendet?

>[!NOTE]
>
>Die Lösungen in [Fehlerbehebung /tmp für Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) sind für Händler konzipiert, die die Variablen für den Datenbank-TMPdir nicht geändert haben, der standardmäßig in `/tmp` geschrieben wird. Wenn Sie den tmpdir-Wert geändert haben, sind die Anweisungen in [Fehlerbehebung /tmp-Bereitstellung für Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) nicht hilfreich.

a. JA - Sie haben das Problem gelöst. \
b. NO - [Senden Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um mehr Platz anzufordern.

+++

## Schritt 5: Standardeinstellung überprüfen {#step-5}

+++**Check default**

Ihre Datenbankkonfiguration befindet sich möglicherweise nicht mehr in der ursprünglichen Standardeinstellung. Suchen Sie die Konfiguration des Datenbank-TMPdir , indem Sie in der CLI [!DNL MySQL] ausführen: `SELECT @@DATADIR;`. Wenn `/data/mysql/` ausgegeben wird, schreibt der Datenbank-TMPdir jetzt in `/data/mysql/`. Versuchen Sie, den Speicherplatz in diesem Verzeichnis zu erhöhen, indem Sie die Schritte unter [[!DNL MySQL] Speicherplatz ist in Adobe Commerce in unserer Cloud-Infrastruktur gering](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) ausführen. Führen Sie dann `df -h | grep mysql` und dann `df -h | grep tmp` in der CLI/Terminal aus, um die Festplattenspeicherplatznutzung in `/data/mysql` und `/tmp` zu überprüfen.\
  &lt; 70 % verwendet?

a. JA - Sie haben das Problem gelöst. \
b. NO - [Senden Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um mehr Platz anzufordern.

+++

[Zurück zu Schritt 1](#step-1)

## Verwandtes Lesen

* [Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung
