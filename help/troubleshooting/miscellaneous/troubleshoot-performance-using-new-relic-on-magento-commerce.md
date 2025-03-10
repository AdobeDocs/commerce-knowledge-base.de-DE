---
title: Fehlerbehebung bei der Leistung mit New Relic auf Adobe Commerce
description: 'Dieser Artikel enthält Schritte zur Fehlerbehebung, um Probleme mit der Leistung von Adobe Commerce in Cloud-Infrastrukturen mit New Relic zu lösen. Es werden auch Ressourcen für weitere Informationen bereitgestellt. Im Folgenden finden Sie eine Liste von Problemen. Klicken Sie hier, um die Schritte zur Fehlerbehebung in unserer Support-Wissensdatenbank anzuzeigen:'
exl-id: 0a22beb7-18b0-47eb-a6b8-63b7322b392c
feature: Observability
role: Developer
source-git-commit: 27fed162416c619a08d757279a3405f1fa72e976
workflow-type: tm+mt
source-wordcount: '901'
ht-degree: 0%

---

# Fehlerbehebung bei der Leistung mit New Relic auf Adobe Commerce

Dieser Artikel enthält Schritte zur Fehlerbehebung, um Probleme mit der Leistung von Adobe Commerce in Cloud-Infrastrukturen mit New Relic zu lösen. Es werden auch Ressourcen für weitere Informationen bereitgestellt. Die folgenden Probleme in der folgenden Tabelle mit empfohlenen Ressourcen werden behandelt:

* Niedriger APDEX-Wert
* Hohe Nutzung von CPU
* Hohe I/O-Operationen
* Ausfall

<table>
<tbody>
<tr>
<td>Problem</td>
<td>Fehlerbehebung</td>
<td>Ressourcen</td>
</tr>
<tr>
<td>
<p>Niedriger APDEX-Wert:</p>
<p>Ihr New Relic <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measuring-user-satisfaction">Apdex-Wert</a> misst die Zufriedenheit der Benutzer mit der Reaktionszeit Ihrer Web-Anwendungen und -Services.</p>
</td>
<td>
<p>Sie melden sich bei <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; Übersicht an. Rechts auf der Übersichtsseite sehen Sie das Apdex-Score-Diagramm. Ein Apdex-Wert von 0,5 oder weniger ist ein Grund zur Sorge und rechtfertigt eine Untersuchung: Web-Transaktionszeiten (Server-Anfragen):</p>
<ol>
<ol>
<li>Melden Sie sich bei <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; (App auswählen) &gt; Übersicht an. Stellen Sie sicher, dass der Filter im Dropdown-Filter Hauptdiagramm auf Webtransaktionszeit eingestellt ist. Suchen Sie unten in der Tabelle Transaktionen nach der Zeit des Anwendungs-Servers. Überprüfen Sie, ob Sie langwierige oder verdächtige Transaktionen haben.</li>
<li>Untersuchen Sie sie einzeln, indem Sie zu Überwachung &gt; Transaktionen gehen und stellen Sie sicher, dass Sie die Filter für Web und am zeitaufwendigsten festlegen<em>.</em>
</li>
<li>Suchen Sie dann nach Drittanbietermodulen, die Ressourcen verbrauchen: Zahlungsdienstleister, ERP usw.</li>
<li>Im Abschnitt Überwachung von APM:<ol>
<li>Klicken Sie auf Transaktionen.</li>
<li>Scrollen Sie nach unten und klicken Sie auf Alle Transaktionen anzeigen .</li>
<li>Sie können Transaktionen nach <a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#table_view">verschiedenen Parametern) sortieren </a> zu den Parametern springen, die einen Verdacht hervorrufen.</li>
<li>Überprüfen Sie diese Transaktionen mit einem niedrigen Apdex-Score, einer ungewöhnlich hohen Anzahl oder einer hohen durchschnittlichen Zeit oder Disset %.</li>
<li>Klicken Sie auf jede einzelne Transaktion. Wenn Sie das Problem nicht beheben können, <a href="/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket">senden Sie ein Support-Ticket.</a>
</li>
<li>Wenn Sie weitere Nachforschungen anstellen müssen, sollten Sie Nicht-Web-Transaktionen überprüfen.</li>
</ol>
</li>
</ol>
</ol>
<p>Nicht-Web-Transaktionszeit (Vorgänge und Hintergrundaufgaben):</p>
<ol>
<ol>
<li>Melden Sie sich bei <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; (App auswählen) &gt; Übersicht an. Stellen Sie sicher, dass Sie im Hauptdiagramm-Dropdown-Filter die Zeit für Nicht-Web-Transaktionen auswählen. Klicken Sie in der Tabelle Transaktionen auf einzelne Transaktionen. Suchen Sie nach langwierigen oder verdächtigen Transaktionen. Dazu gehören Backend-, Cron- oder Import-/Exportvorgänge, einschließlich Drittanbietervorgänge.</li>
</ol>
</ol>
</td>
<td>
<p>Weitere Informationen zum New Relic Apdex-Score finden Sie in der <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction">New Relic-Dokumentation &gt; APM Apdex &gt; Messung der Benutzerzufriedenheit</a>. Weitere Informationen finden Sie unter <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-apdex-warning-alert">Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis zu Apdex</a> in unserer Support-Wissensdatenbank.</p>
</td>
</tr>
<tr>
<td>
<p>Hohe CPU-Nutzung:</p>
<p>Eine hohe Nutzung von CPU kann darauf hinweisen, dass es einen besonders stark ausgelasteten Dienst gibt, z. B. MySQL, Redis usw.</p>
</td>
<td>
<ol>
<li>Melden Sie sich bei <a href="https://login.newrelic.com/login">New Relic</a> &gt; Infrastruktur &gt; Prozesse an.</li>
<li>Überprüfen Sie die CPU-Diagramme, um festzustellen, ob ein Prozess stecken geblieben ist oder mehr als 100 % CPU-Zeit in Anspruch nimmt, und vergleichen Sie diese mit der Prozessoranzahl in der Instanz. Achten Sie auf Spitzen in der Ressourcenauslastung. Es wird nicht empfohlen, einen Prozess zu beenden, es sei denn, es handelt sich um einen steckengebliebenen Cron.</li>
</ol>
</td>
<td>
<p>Weitere Informationen zu Leistungsmetriken, insbesondere CPU-Prozentsatz, E/A-Bytes und Speichernutzung für einzelne oder Gruppen von Prozessen, finden Sie unter <a href="https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes">New Relic-Dokumentation &gt; Seite zur Infrastruktur-Benutzeroberfläche &gt; Seite „Infrastruktur-Host“ &gt; Registerkarte „Prozesse“</a>.</p>
</td>
</tr>
<tr>
<td>
<p>Hohe E/A-Vorgänge: Für jeden Kunden ist diese Zahl individuell, unterscheidet sich jedoch erheblich vom Durchschnitt.</p>
</td>
<td>
<p>Achten Sie auf eine ungewöhnliche Spitze im Vergleich zu früheren durchschnittlichen I/O-Vorgängen:</p>
<ol>
<li>Melden Sie sich bei <a href="https://login.newrelic.com/login">New Relic</a> &gt; Infrastruktur &gt; Prozesse an.</li>
<li>Überprüfen Sie das Diagramm I/O-Lesebytes pro Sekunde.</li>
<li>Notieren Sie den Zeitpunkt der Spitze.</li>
<li>Klicken Sie auf APM.</li>
<li>Stellen Sie sicher, dass Sie im Hauptdiagramm-Dropdown-Filter die Zeit für Web-Transaktionen auswählen.</li>
<li>Legen Sie die Zeit für die Zeit der aufgezeichneten Spitze fest.</li>
<li>Suchen Sie nach Transaktionen, die hohe I/O-Operationen verursacht haben.</li>
<li>Drilldown für jede Transaktions-Trace &gt; Trace-Details , um herauszufinden, was möglicherweise Probleme verursacht.</li>
</ol>
</td>
</tr>
<tr>
<td>
<p>Ausfall: New Relic ermittelt Ausfälle durch Apdex. Im Apdex-Score-Diagramm wird eine rote Linie angezeigt, die auf einen Apdex &lt; 0,4 hinweist, der als Ausfall betrachtet wird.</p>
</td>
<td>
<p>Die Untersuchung eines Ausfalls kann mehrere Schritte umfassen, um Web- und Nicht-Web-Transaktionen, Datenbanken und Transaktionen von Drittanbietern zu untersuchen. Web-Transaktionen:</p>
<ol>
<li>Melden Sie sich bei <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; Übersicht an. Stellen Sie sicher, dass der Filter im Dropdown-Diagrammfilter auf Webtransaktionszeit eingestellt ist.</li>
<li>Schränken Sie das Zeitfenster manuell ein.</li>
<li>Klicken Sie auf Transaktionen. Stellen Sie sicher, dass die Filter auf Web eingestellt sind und am zeitaufwendigsten sind. Untersuchen Sie die Transaktion mit der längsten Laufzeit.</li>
<li>Wenn Sie weitere Nachforschungen anstellen müssen, sollten Sie Nicht-Web-Transaktionen überprüfen.</li>
</ol>
<p>Nicht-Web-Transaktionen:</p>
<ol>
<li>Kehren Sie zur Seite Überblick zurück und wechseln Sie im Dropdown-Filter zu Nicht-Web-Transaktionen .</li>
<li>Überprüfen Sie die Transaktionsnachweise ganz unten auf der Seite einzeln.</li>
<li>Je nach Problem müssen Sie möglicherweise ein Drittanbieter-Tool wie einen PHP-Profiler verwenden, um einen Engpass zu finden.</li>
<li>Wenn Sie weitere Nachforschungen anstellen müssen, sollten Sie die Datenbankprozesse überprüfen.</li>
</ol>
<p>Datenbankprozesse:</p>
<ol>
<li>Gehen Sie auf der Seite „APM“ zu Überwachung &gt; Datenbanken.</li>
<li>Sortieren Sie nach dem zeitaufwendigsten.</li>
<li>TOP-Abfragen überprüfen.

Hinweis: <code>UPDATE</code> oder <code>EINFÜGEN</code>Abfragen sind die CPU-intensivsten Abfragen.</li>
<li>Wechseln Sie von der Auswahl Sortieren nach zu Durchsatz und suchen Sie nach Prozessen, die zu einer Dropdown-Liste „Datenbankdurchsatz“ geführt haben.</li>
<li>Wenn Sie weitere Nachforschungen anstellen müssen, sollten Sie die Services von Drittanbietern in Erwägung ziehen.</li>
</ol>
<p>Services von Drittanbietern:</p>
<ol>
<li>Wechseln Sie auf der Seite „APM“ zu Überwachung &gt; Externe Dienste .</li>
<li>Wählen Sie in der Dropdown-Liste Sortieren nach die langsamste durchschnittliche Antwortzeit aus.</li>
<li>Suchen Sie nach Prozessen, die unmittelbar vor dem Ausfall aufgetreten sind.</li>
</ol>
</td>
<td>
<p>Weitere Informationen zur Untersuchung bestimmter Leistungsprobleme finden Sie unter <a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#tx_functions">New Relic-Dokumentation &gt; Seiten der APM-Benutzeroberfläche &gt; Transaktionsseite &gt; Verwenden von Aufschlüsselungsfunktionen</a>.</p>
</td>
</tr>
</tbody>
</table>
