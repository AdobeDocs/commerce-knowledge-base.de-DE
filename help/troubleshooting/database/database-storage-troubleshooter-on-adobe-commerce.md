---
title: Fehlerbehebung bei der Datenbankspeicherung in Adobe Commerce
description: Dieser Artikel ist ein Tool zur Fehlerbehebung für Kunden und Kundinnen, die Probleme mit Adobe Commerce-Datenbanken haben. Klicken Sie auf die einzelnen Fragen, um die Antwort in jedem Schritt der Fehlerbehebung anzuzeigen. Abhängig von Ihren Symptomen und Ihrer Konfiguration erklärt die Fehlerbehebung, wie Sie Speicherplatzprobleme und Konfigurationsprobleme mit Datenbanken beheben.
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: aa4cfbceb745f1a06b8a8f9e93cbdebbc151458b
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 0%

---

# Fehlerbehebung bei der Datenbankspeicherung in Adobe Commerce

Dieser Artikel ist ein Tool zur Fehlerbehebung für Kunden und Kundinnen, die Probleme mit Adobe Commerce-Datenbanken haben. Klicken Sie auf die einzelnen Fragen, um die Antwort in jedem Schritt der Fehlerbehebung anzuzeigen. Abhängig von Ihren Symptomen und Ihrer Konfiguration erklärt die Fehlerbehebung, wie Sie Speicherplatzprobleme und Konfigurationsprobleme mit Datenbanken beheben.

## Schritt 1: Identifizieren des Ordners mit einem Leerzeichen-Problem {#step-1}

+++**Haben Sie ein `/tmp` Problem, das durch Platzmangel verursacht wurde?**

Dies kann an einer Reihe von Symptomen erkennbar sein, z. B. dass die `/tmp`-Mount voll ist, sich nicht an der Site befindet oder nicht in der Lage ist, SSH in einen -Knoten zu integrieren. Möglicherweise treten auch Fehler auf wie _Kein Platz mehr auf dem Gerät (28)_. Eine Liste der Fehler, die sich daraus ergeben, dass `/tmp` voll ist, finden Sie unter [/tmp mount full](/help/troubleshooting/miscellaneous/tmp-mount-full.md).

Oder haben Sie ein `/data/mysql` Problem, das durch Platzmangel verursacht wurde? Dies kann auch durch eine Vielzahl von Symptomen angezeigt werden, darunter Website-Ausfall, Kunden, die keine Produkte in den Warenkorb legen können, Verbindungsfehler zur Datenbank und Galeria-Fehler wie _SQLSTATE\[08S01\]: Kommunikationsverbindungsfehler: 1047 WSREP_. Eine Liste der Fehler, die aus zu wenig [!DNL MySQL] Speicherplatz resultieren, finden Sie unter [[!DNL MySQL] Speicherplatz ist in Adobe Commerce auf der Cloud-Infrastruktur zu niedrig](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27806).

Wenn Sie sich nicht sicher sind, ob Sie ein Speicherplatzproblem haben und ein New Relic-Konto haben, gehen Sie zur Seite [Hosts für die Überwachung der New Relic-Infrastruktur](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/). Klicken Sie dort auf die Registerkarte **Speicher**, ändern Sie die Dropdown-Liste **Diagramme** von 5 bis 20 Ergebnissen und suchen Sie in der Tabelle nach einer hohen Festplattenauslastung im Diagramm oder in der Tabelle Verwendete Festplatte % . Weitere Informationen finden Sie unter [New Relic-Infrastrukturüberwachung > Registerkarte „Speicher“]https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage).

Wenn Sie eines der oben beschriebenen Symptome haben, überprüfen Sie den Status Ihrer Inodes, um sicherzustellen, dass dies nicht durch Probleme mit der Dateinummer verursacht wird. Führen Sie dazu den folgenden Befehl in der CLI/Terminal aus:\
`df -ih`

Ist IUse% > 90%?

a. JA - Dies liegt daran, dass zu viele Dateien vorhanden sind. Überprüfen Sie die Schritte zum sicheren Entfernen von Dateien in [Dateien sicher löschen, wenn kein Speicherplatz mehr zur Verfügung steht, Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26889). Fahren Sie [&#x200B; Schritt 2 fort](#step-2) nachdem Sie diese Schritte abgeschlossen haben. Wenn Sie mehr Speicherplatz benötigen, reichen [ein Support-Ticket ein](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NEIN - Platzierung prüfen. Führen Sie `df -h | grep mysql` und dann `df -h | grep tmp` in der CLI/Terminal aus, um die Speicherplatznutzung in den `/tmp`- und `/data/mysql`-Verzeichnissen zu überprüfen. Fahren Sie mit [Schritt 3](#step-3) fort.

+++

## Schritt 2: Überprüfen Sie den Festplattenspeicher. {#step-2}

+++**Überprüfen Sie die Speicherplatznutzung?**

Nachdem Sie die Anzahl der Dateien reduziert haben, führen Sie `df -h | grep mysql` aus und `df -h | grep tmp` Sie dann in der CLI/Terminal, um den Speicherplatzbedarf in `/tmp` und `/data/mysql` zu überprüfen. Werden für `/tmp` oder `/data/mysql` mehr als 70 % verwendet?

a. JA - Mit [Schritt 3](#step-3) fortfahren.
b. NEIN - Abfragen können den verfügbaren Speicher erschöpfen. Dadurch kann der Knoten abstürzen, die Abfrage wird beendet und die `tmp` Dateien werden entfernt. Untersuchen Sie die Ausgabe des `SHOW PROCESSLIST;` in der [!DNL MySQL] CLI auf Abfragen, die die Ursache des Problems sein könnten. [Senden Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) und benötigen Sie mehr Speicherplatz.

+++

## Schritt 3: Identifizieren des Ordners mit hoher Nutzung {#step-3}

+++**Welches Verzeichnis wird zu mehr als 70 % verwendet?**

Welches Verzeichnis wird zu mehr als 70 % verwendet? `/tmp` oder `/data/mysql`?

>[!NOTE]
>
>Standardmäßig schreibt Datenbank-tmpdir in `/tmp`. Um zu überprüfen, ob Ihre Datenbankkonfiguration immer noch auf dieser Standardeinstellung ist, führen Sie den folgenden Befehl in [!DNL MySQL] CLI aus: `SHOW VARIABLES LIKE "TMPDIR";` Wenn das Datenbank-tmpdir immer noch in `/tmp` schreibt, wird in der Spalte Wert `/tmp` angezeigt.

a. `/tmp` - Fahren Sie mit [Schritt 4](#step-4) fort. \
b. `/data/mysql` - Fahren Sie mit [Schritt 5](#step-5) fort.

+++

## Schritt 4: Fehlerbehebung bei der vollständigen /tmp-Bereitstellung {#step-4}

+++**Fehlerbehebung bei der /tmp-Bereitstellung vollständig**

[Fehlerbehebung bei /tmp-Bereitstellungen für Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md), scrollen Sie im Artikel nach unten und versuchen Sie die Lösungen und Best Practices. Führen Sie dann `df -h | grep mysql` aus und `df -h | grep tmp` Sie dann in der CLI/Terminal, um die Speicherplatznutzung in `/tmp`- und `/data/mysql`-Verzeichnissen zu überprüfen\
  &lt; 70% verwendet?

>[!NOTE]
>
>Die Lösungen in [Fehlerbehebung /tmp mount full für Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) sind für Händler konzipiert, die die Variablen für die Datenbank tmpdir, die standardmäßig in `/tmp` schreibt, nicht geändert haben. Wenn Sie den Wert „tmpdir“ geändert haben, helfen die Anweisungen unter [Fehlerbehebung bei /tmp-Bereitstellungen für Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) nicht weiter.

a. JA - Sie haben das Problem gelöst. \
b. NEIN - [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) mehr Platz benötigen.

+++

## Schritt 5 - Standard überprüfen {#step-5}

+++**Standard überprüfen**

Die Datenbankkonfiguration befindet sich möglicherweise nicht mehr auf dem ursprünglichen Standardwert. Suchen Sie die Datenbank-tmpdir-Konfiguration, indem Sie in der [!DNL MySQL] CLI ausführen: `SELECT @@DATADIR;`. Wenn `/data/mysql/` ausgegeben wird, schreibt die Datenbank tmpdir jetzt in `/data/mysql/`. Versuchen Sie, den Speicherplatz in diesem Verzeichnis zu erhöhen, indem Sie die Schritte unter [[!DNL MySQL] Speicherplatz ist auf Adobe Commerce in unserer Cloud-Infrastruktur knapp](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27806) befolgen. Führen Sie dann `df -h | grep mysql` aus und `df -h | grep tmp` Sie dann in der CLI/Terminal, um die Speicherplatznutzung in `/data/mysql` und `/tmp` zu überprüfen.\
  &lt; 70% verwendet?

a. JA - Sie haben das Problem gelöst. \
b. NEIN - [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) mehr Platz benötigen.

+++

[Zurück zu Schritt 1](#step-1)

## Verwandtes Lesen

* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
