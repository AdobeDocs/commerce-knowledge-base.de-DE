---
title: Fehlerbehebung bei New Relic auf Adobe Commerce in der Cloud-Infrastruktur
description: Dieser Artikel enthält Ressourcen zur Fehlerbehebung bei New Relic in Adobe Commerce in der Cloud-Infrastruktur.
exl-id: ea763291-5c9b-4575-b2ee-820dbc367743
feature: Cloud, Observability, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Fehlerbehebung bei New Relic auf Adobe Commerce in der Cloud-Infrastruktur

Dieser Artikel enthält Ressourcen zur Fehlerbehebung bei New Relic in Adobe Commerce in der Cloud-Infrastruktur.

<table>
<tbody>
<tr>
<td class="wysiwyg-text-align-center"><strong>Problem</strong></td>
<td class="wysiwyg-text-align-center"><strong>Ursache</strong></td>
<td class="wysiwyg-text-align-center"><strong>Ressourcen</strong></td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">Zugriffsprobleme</td>
</tr>
<tr>
<td>
<p><u>Projekte in New Relic können nicht angezeigt werden.</u></p>
<p>Sie melden sich bei <em>New Relic</em> an, können jedoch keine Projekte anzeigen, für die Sie berechtigt sein sollten, darauf zuzugreifen.</p>
</td>
<td>
<p>In diesen Fällen muss ein Administrator Sie zum Projekt hinzufügen.</p>
</td>
<td>
<p><a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html">Zugriff auf New Relic-Dienste</a> in unserer Wissensdatenbank.</p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">Datenprobleme</td>
</tr>
<tr>
<td>
<p><u>Fehlende Daten nach der Installation.</u></p>
<p>Verwenden Sie das Dienstprogramm <a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/new-relic-diagnostics">New Relic Diagnostics</a>, um die Ursache zu ermitteln. Wenn dies nicht hilfreich ist, sollten Sie sich agentenspezifische Lösungen ansehen. Links zu Artikeln, die diese Lösungen enthalten, befinden sich in der rechten Spalte.</p>
</td>
<td>
<p>Fehlende Daten können unterschiedliche Ursachen haben. Möglicherweise müssen Sie:</p>
<ul>
<li>Überprüfen Sie, ob der Agent installiert ist.</li>
<li>Überprüfen Sie Ihren App-Namen und Ihren Lizenzschlüssel.</li>
<li>Starten Sie den Webserver neu.</li>
<li>Stellen Sie sicher, dass Ihr System die Kompatibilitätsanforderungen erfüllt.</li>
<li>INI-Einstellungen.</li>
</ul>
</td>
<td>
<ul>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#apm-agents">New Relic-Dokumentation &gt; APM-Agenten &gt; Keine Daten anzeigen</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#browser-agent">New Relic-Dokumentation &gt; New Relic-Browser &gt; Nicht anzeigen von Daten</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#infrastructure-agents">New Relic-Dokumentation &gt; New Relic-Infrastruktur &gt; Nicht anzeigen von Daten</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#mobile-agents">New Relic-Dokumentation &gt; New Relic Mobile &gt; Keine Daten anzeigen</a></li>
</ul>
</td>
</tr>
<tr>
<td>
<p><u>Diskrepanz bei Transaktionszeitstempeln.</u> Sie können mit der New Relic-Benutzeroberfläche Schwierigkeiten haben, lange Transaktionen (mehr als 5 Minuten) zu finden. Sie können auch Transaktionen finden, die außerhalb des erwarteten Zeitrahmens angezeigt werden.</p>
</td>
<td>
<p>In der New Relic-Benutzeroberfläche wird der Zeitpunkt des Transaktionsendes und nicht der Zeitpunkt des Transaktionsbeginns angezeigt.</p>
</td>
<td>
<p>Um den Anfang der Transaktion mithilfe der New Relic-Benutzeroberfläche zu berechnen, überprüfen Sie die Dauer der Transaktion. Ziehen Sie den Betrag der Dauer vom Zeitstempel (Transaktionsende) ab, der von der Benutzeroberfläche von New Relic bereitgestellt wird.</p>
</td>
</tr>
<tr>
<td>
<p><u>NerdGraph GraphQL <code>curl</code> Abfragen mit Sonderzeichen wie <code>|</code> und <code>%</code> funktionieren nicht</u>.</p>
</td>
<td>
<p>Die New Relic-Funktion "Copy to curl"in NerdGraph bietet derzeit keine Möglichkeit, Sonderzeichen wie <code>|</code> und <code>%</code> zu verarbeiten.</p>
</td>
<td>
<p>Verwenden Sie eine andere API-Bibliothek, um das Problem mit Sonderzeichen zu lösen. Beispiel: GraphQLClient-Bibliothek für GraphQL-API in Python oder Apache.commons nach Java-Sprachaufrufen. Überprüfen Sie Client-Bibliotheken auf <a href="https://graphql.org/code/">GraphQL</a>.</p>
</td>
</tr>
<tr>
<td>
<p><u>Anzeigeprobleme mit Diagrammen und Dashboards</u></p>
</td>
<td>
<p>Beheben Sie fehlende Diagramme, indem Sie New Relic-Domänen zur Zulassungsliste hinzufügen oder die Browsererweiterung deinstallieren, was zu Problemen führt.</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/apm/new-relic-apm/troubleshooting/charts-missing-or-do-not-render">New Relic-Dokumentation &gt; Diagramme fehlen oder nicht rendern</a> </p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">Probleme mit PHP-Agenten</td>
</tr>
<tr>
<td>
<p><u>Der PHP Agent zeigt nicht die richtige Instanzanzahl an.</u></p>
</td>
<td>
<p>Die Anzahl der Instanzen kann in Abhängigkeit von Back-End-Prozessen und -Durchsatz steigen. Unterschiede zwischen Serverwerten können auf Prozesse zurückzuführen sein, die auf einem Server, aber nicht auf dem anderen Server ausgeführt werden.</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/agents/php-agent/troubleshooting/troubleshoot-php-agent-instance-count">New Relic-Dokumentation &gt; Fehlerbehebung bei der Anzahl der PHP-Agent-Instanzen</a> </p>
</td>
</tr>
</tbody>
</table>
