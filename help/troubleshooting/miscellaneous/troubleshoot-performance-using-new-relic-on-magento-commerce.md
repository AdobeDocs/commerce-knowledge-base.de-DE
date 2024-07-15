---
title: Fehlerbehebung bei der Leistung von New Relic auf Adobe Commerce
description: '"Dieser Artikel enthält Schritte zur Fehlerbehebung bei Adobe Commerce zur Lösung von Problemen mit der Cloud-Infrastruktur-Performance mithilfe von New Relic. Es stellt auch Ressourcen für weitere Informationen bereit. Im Folgenden finden Sie eine Liste der Probleme. Klicken Sie auf , um die Schritte zur Fehlerbehebung in unserer Support-Wissensdatenbank zu sehen:'''
exl-id: 0a22beb7-18b0-47eb-a6b8-63b7322b392c
feature: Observability
role: Developer
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 0%

---

# Fehlerbehebung bei der Leistung von New Relic auf Adobe Commerce

In diesem Artikel finden Sie Schritte zur Fehlerbehebung bei Problemen mit der Cloud-Infrastruktur-Performance von Adobe Commerce mit New Relic. Es stellt auch Ressourcen für weitere Informationen bereit. Folgende Probleme werden in der folgenden Tabelle mit empfohlenen Ressourcen behandelt:

* Niedriges Apdex-Ergebnis
* Hohe CPU-Auslastung
* Hoher I/O-Betrieb
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
<p>Niedriger Apdex-Wert:</p>
<p>Der New Relic-Wert <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measuring-user-satisfaction">Apdex-Wert</a> misst die Zufriedenheit der Benutzer mit der Reaktionszeit Ihrer Webanwendungen und -dienste.</p>
</td>
<td>
<p>Sie melden sich bei <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; Übersicht an. Auf der rechten Seite der Übersichtsseite sehen Sie das Apdex-Punktdiagramm. Ein Apdex-Wert von 0,5 oder weniger ist ein Grund zur Besorgnis und erfordert die Untersuchung: Web-Transaktionszeiten (Server-Anforderungen):</p>
<ol>
<ol>
<li>Melden Sie sich bei <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; (App auswählen) &gt; Übersicht an. Stellen Sie sicher, dass der Filter im Dropdown-Filter für Hauptdiagramme auf Webtransaktionszeit eingestellt ist. Suchen Sie unten in der Transaktionstabelle nach der Zeit des Anwendungsservers. Überprüfen Sie, ob Sie über langwierige oder verdächtige Transaktionen verfügen.</li>
<li>Untersuchen Sie sie einzeln, indem Sie zu Überwachung &gt; Transaktionen navigieren und stellen Sie sicher, dass Sie die Filter für Web und die zeitintensivsten<em> festlegen.</em>
</li>
<li>Suchen Sie dann nach Drittanbietermodulen, die Ressourcen verbrauchen: Zahlungsdienstleister, ERP usw.</li>
<li>Im Abschnitt Überwachung von APM:<ol>
<li>Klicken Sie auf Transaktionen.</li>
<li>Scrollen Sie nach unten und klicken Sie auf Alle Transaktionen anzeigen .</li>
<li>Sie können Transaktionen nach <a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#table_view">verschiedenen Parametern</a> sortieren und zu den Parametern springen, die Verdacht verursachen.</li>
<li>Überprüfen Sie diese Transaktionen mit einem niedrigen Apdex-Wert, ungewöhnlich hoher Count- oder hoher Avg-Zeit oder Dissat %.</li>
<li>Klicken Sie auf jede einzelne Transaktion. Wenn Sie das Problem nicht beheben können, senden <a href="/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket">ein Support-Ticket.</a>
</li>
<li>Wenn Sie weitere Untersuchungen durchführen müssen, sollten Sie Nicht-Web-Transaktionen überprüfen.</li>
</ol>
</li>
</ol>
</ol>
<p>Nicht-Webtransaktionszeit (Vorgänge und Hintergrundaufgaben):</p>
<ol>
<ol>
<li>Melden Sie sich bei <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; (App auswählen) &gt; Übersicht an. Stellen Sie sicher, dass Sie im Dropdown-Filter für Hauptdiagramme die Option Zeit für Nicht-Web-Transaktionen auswählen. Klicken Sie in der Transaktionstabelle auf die einzelnen Transaktionen. Suchen Sie nach langwierigen oder verdächtigen Transaktionen. Dies umfasst Backend-Aufträge, Cron-Aufträge oder Import-/Exportvorgänge, einschließlich Drittanbieter-Aufträgen.</li>
</ol>
</ol>
</td>
<td>
<p>Weitere Informationen zum New Relic-Apdex-Ergebnis finden Sie in der <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction">New Relic-Dokumentation &gt; APM-Apdex &gt; Benutzerzufriedenheit messen</a>. Sie können auch auf <a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md">Verwalte Warnhinweise für Adobe Commerce: Warnhinweis für Index</a> in unserer Support-Wissensdatenbank verweisen.</p>
</td>
</tr>
<tr>
<td>
<p>Hohe CPU-Auslastung:</p>
<p>Eine hohe CPU-Auslastung kann darauf hinweisen, dass ein besonders ausgelasteter Dienst wie MySQL, Redis usw. vorhanden ist.</p>
</td>
<td>
<ol>
<li>Melden Sie sich bei <a href="https://login.newrelic.com/login">New Relic</a> &gt; Infrastruktur &gt; Prozesse an.</li>
<li>Überprüfen Sie die CPU-Diagramme, um festzustellen, ob ein steckender oder hochauflösender Prozess vorhanden ist, der mehr als 100 % CPU-Zeit verwendet, und vergleichen Sie ihn mit der Prozessoranzahl der Instanz. Achten Sie auf Spitzen bei der Ressourcenauslastung. Es wird nicht empfohlen, einen Prozess zu beenden, es sei denn, es handelt sich um einen hängenden Cron.</li>
</ol>
</td>
<td>
<p>Weitere Informationen zu Leistungsmetriken, insbesondere zum CPU-Prozentsatz, zu I/O-Bytes und zur Speichernutzung für einzelne oder Gruppen von Prozessen, finden Sie unter <a href="https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes">New Relic-Dokumentation &gt; Infrastruktur-UI-Seite &gt; Infrastruktur-Host-Seite &gt; Registerkarte "Prozesse"</a>.</p>
</td>
</tr>
<tr>
<td>
<p>Hoher I/O-Betrieb: Für jeden Kunden wäre diese Zahl individuell, unterscheidet sich jedoch erheblich vom Durchschnitt.</p>
</td>
<td>
<p>Suchen Sie nach einer ungewöhnlichen Spitze im Vergleich zu vorherigen durchschnittlichen I/O-Vorgängen:</p>
<ol>
<li>Melden Sie sich bei <a href="https://login.newrelic.com/login">New Relic</a> &gt; Infrastruktur &gt; Prozesse an.</li>
<li>Prüfen Sie die I/O-Lesezeichen pro Sekunde.</li>
<li>Zeichnen Sie die Zeit der Spitze auf.</li>
<li>Klicken Sie auf APM.</li>
<li>Stellen Sie sicher, dass Sie im Dropdown-Filter für Hauptdiagramme die Zeit der Webtransaktionen auswählen.</li>
<li>Legen Sie die Zeit für die Zeit der aufgezeichneten Spitze fest.</li>
<li>Suchen Sie nach Transaktionen, die zu hohen E/A-Vorgängen geführt haben.</li>
<li>Führen Sie einen Drilldown in die einzelnen Transaktions-Trace-Details durch, um zu finden, was Probleme verursachen könnte.</li>
</ol>
</td>
</tr>
<tr>
<td>
<p>Ausfall: New Relic ermittelt Ausfälle nach Apdex. Im Apdex-Punktdiagramm wird eine rote Linie angezeigt, die auf Apdex &lt; 0,4 hinweist, was als Ausfall gilt.</p>
</td>
<td>
<p>Die Untersuchung eines Ausfalls kann mehrere Schritte umfassen, um Web- und Nicht-Web-Transaktionen, Datenbanken und Transaktionen mit Dritten zu untersuchen. Web-Transaktionen:</p>
<ol>
<li>Melden Sie sich bei <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; Übersicht an. Stellen Sie sicher, dass der Filter im Dropdown-Diagrammfilter auf Webtransaktionen-Zeit eingestellt ist.</li>
<li>Das Zeitfenster manuell eingrenzen.</li>
<li>Klicken Sie auf Transaktionen. Stellen Sie sicher, dass die Filter auf "Web"und "Am zeitintensivsten"eingestellt sind. Untersuchen Sie die am längsten laufende Transaktion.</li>
<li>Wenn Sie weitere Untersuchungen durchführen müssen, sollten Sie Nicht-Web-Transaktionen überprüfen.</li>
</ol>
<p>Nicht-Web-Transaktionen:</p>
<ol>
<li>Gehen Sie zurück zur Seite Übersicht und wechseln Sie im Dropdown-Filter zu Nicht-Web-Transaktionen .</li>
<li>Überprüfen Sie die Transaktionsnachverfolgung am unteren Rand der Seite, einzeln.</li>
<li>Je nach Problem müssen Sie möglicherweise ein Tool eines Drittanbieters wie einen PHP Profiler verwenden, um einen Engpass zu finden.</li>
<li>Wenn Sie weitere Untersuchungen durchführen müssen, sollten Sie Datenbankprozesse prüfen.</li>
</ol>
<p>Datenbankprozesse:</p>
<ol>
<li>Gehen Sie auf der APM-Seite zu Monitoring &gt; Datenbanken.</li>
<li>Sortieren nach am zeitaufwendigsten.</li>
<li>Überprüfen Sie die TOP-Abfragen.

Hinweis: <code>UPDATE</code> oder <code>INSERT</code>Abfragen sind die CPU-intensivsten Abfragen.</li>
<li>Wechseln Sie von Sortieren nach Auswahl zu Durchsatz und suchen Sie nach Prozessen, die zu einer Dropdown-Liste des Datenbankdurchsatzes geführt haben.</li>
<li>Wenn Sie weitere Untersuchungen durchführen müssen, sollten Sie die Services von Drittanbietern prüfen.</li>
</ol>
<p>Drittanbieterdienste:</p>
<ol>
<li>Gehen Sie auf der APM-Seite zu Monitoring &gt; Externe Dienste .</li>
<li>Wählen Sie aus der Dropdownliste Sortieren nach die langsamste durchschnittliche Reaktionszeit aus.</li>
<li>Suchen Sie nach Prozessen, die unmittelbar vor dem Ausfall aufgetreten sind.</li>
</ol>
</td>
<td>
<p>Weitere Informationen zur Untersuchung bestimmter Leistungsprobleme finden Sie unter <a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#tx_functions">New Relic-Dokumentation &gt; Seiten der APM-Benutzeroberfläche &gt; Seite Transaktionen &gt; Drilldown-Funktionen verwenden</a>.</p>
</td>
</tr>
</tbody>
</table>
