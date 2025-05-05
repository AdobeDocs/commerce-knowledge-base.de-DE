---
title: Fehlerbehebung bei New Relic in Adobe Commerce auf Cloud-Infrastruktur
description: Dieser Artikel enthält Ressourcen zur Fehlerbehebung bei New Relic in Adobe Commerce in Cloud-Infrastrukturen.
exl-id: ea763291-5c9b-4575-b2ee-820dbc367743
feature: Cloud, Observability, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Fehlerbehebung bei New Relic in Adobe Commerce auf Cloud-Infrastruktur

Dieser Artikel enthält Ressourcen zur Fehlerbehebung bei New Relic in Adobe Commerce in Cloud-Infrastrukturen.

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
<p><u>Projekte in New Relic werden nicht angezeigt.</u></p>
<p>Sie melden sich bei <em>New Relic an</em> sehen jedoch keine Projekte, für die Sie über die Berechtigung zum Anzeigen/Zugreifen verfügen.</p>
</td>
<td>
<p>In diesen Fällen muss Sie ein Administrator bzw. eine Administratorin zum Projekt hinzufügen.</p>
</td>
<td>
<p><a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html?lang=de">Zugriff auf New Relic-</a> in unserer Support-Wissensdatenbank.</p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">Datenprobleme</td>
</tr>
<tr>
<td>
<p><u>Fehlende Daten nach der Installation.</u></p>
<p>Mit dem <a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/new-relic-diagnostics">New Relic-Diagnosedienstprogramm</a> können Sie die Ursache ermitteln. Wenn dies nicht hilfreich ist, schauen Sie sich die agentenspezifischen Lösungen an. Links zu Artikeln, die diese Lösungen enthalten, finden Sie in der rechten Spalte.</p>
</td>
<td>
<p>Fehlende Daten können unterschiedliche Ursachen haben. Möglicherweise müssen Sie:</p>
<ul>
<li>Stellen Sie sicher, dass der Agent installiert ist.</li>
<li>Überprüfen Sie Ihren App-Namen und Ihren Lizenzschlüssel.</li>
<li>Starten Sie den Webserver neu.</li>
<li>Stellen Sie sicher, dass Ihr System die Kompatibilitätsanforderungen erfüllt.</li>
<li>INI-Einstellungen.</li>
</ul>
</td>
<td>
<ul>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#apm-agents">New Relic-Dokumentation &gt; APM-Agenten &gt; Daten werden nicht angezeigt</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#browser-agent">New Relic-Dokumentation &gt; New Relic-Browser &gt; Daten werden nicht angezeigt</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#infrastructure-agents">New Relic-Dokumentation &gt; New Relic-Infrastruktur &gt; Daten werden nicht angezeigt</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#mobile-agents">New Relic-Dokumentation &gt; New Relic Mobile &gt; Daten werden nicht angezeigt</a></li>
</ul>
</td>
</tr>
<tr>
<td>
<p><u>Diskrepanz beim Transaktionszeitstempel.</u> Sie können Schwierigkeiten haben, lange Transaktionen (mehr als 5 Minuten) über die New Relic-Benutzeroberfläche zu finden. Möglicherweise werden auch Transaktionen außerhalb des erwarteten Zeitraums angezeigt.</p>
</td>
<td>
<p>Die New Relic-Benutzeroberfläche zeigt den Zeitpunkt des Transaktionsendes an, nicht den Zeitpunkt, zu dem die Transaktion begann.</p>
</td>
<td>
<p>Um den Beginn der Transaktion mithilfe der New Relic-Benutzeroberfläche zu berechnen, überprüfen Sie die Dauer der Transaktion. Ziehen Sie den Dauerbetrag vom Zeitstempel (Transaktionsende) ab, der von der New Relic-Benutzeroberfläche bereitgestellt wird.</p>
</td>
</tr>
<tr>
<td>
<p><u>NerdGraph GraphQL <code>curl</code> Abfragen mit Sonderzeichen wie <code>|</code> und <code>%</code> funktionieren nicht</u>.</p>
</td>
<td>
<p>Die New Relic-Funktion „Kopieren in cURL“ in NerdGraph bietet derzeit keine Möglichkeit, Sonderzeichen wie <code>|</code> und <code>%</code> zu verarbeiten.</p>
</td>
<td>
<p>Verwenden Sie eine andere API-Bibliothek, um das Problem mit Sonderzeichen zu lösen. Beispielsweise die GraphQL-Client-Bibliothek für die GraphQL-API in Python oder Apache.commons nach Java-Sprachaufrufen. Überprüfen Sie Client-Bibliotheken auf <a href="https://graphql.org/code/">GraphQL</a>.</p>
</td>
</tr>
<tr>
<td>
<p><u>Probleme in Diagrammen und Dashboards anzeigen.</u></p>
</td>
<td>
<p>Beheben Sie fehlende Diagramme, indem Sie der Zulassungsliste New Relic-Domains hinzufügen oder die Browser-Erweiterung deinstallieren, was die Probleme verursacht.</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/apm/new-relic-apm/troubleshooting/charts-missing-or-do-not-render">New Relic-Dokumentation &gt; Diagramme fehlen oder werden nicht gerendert</a> </p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">Probleme mit PHP-Agenten</td>
</tr>
<tr>
<td>
<p><u>Der PHP-Agent zeigt nicht die richtige Anzahl an Instanzen an.</u></p>
</td>
<td>
<p>Die Anzahl der Instanzen kann je nach Back-End-Prozessen und Durchsatz steigen. Unterschiede zwischen den Server-Werten können durch Prozesse verursacht werden, die auf einem Server ausgeführt werden, aber nicht auf dem anderen Server.</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/agents/php-agent/troubleshooting/troubleshoot-php-agent-instance-count">New Relic-Dokumentation &gt; Fehlerbehebung bei der PHP-Agenteninstanzanzahl</a> </p>
</td>
</tr>
</tbody>
</table>
