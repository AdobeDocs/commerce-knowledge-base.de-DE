---
title: 'Web Application Firewall (WAF) powered by Fastly: die FAQ'
description: Web Application Firewalls (WAFs) verhindern, dass bösartiger Traffic in Sites und Netzwerke eindringt, indem sie den Traffic nach einer Reihe von Sicherheitsregeln filtern. Traffic, der Trigger einer der Regeln ist, wird blockiert, bevor er Ihre Websites oder Ihr Netzwerk beschädigen kann.
exl-id: d977ea68-7d8c-4863-b026-acdc25d8c430
feature: Cache
source-git-commit: f384ff9d5d8a8c5c5da20b582c02a2d783b32d7e
workflow-type: tm+mt
source-wordcount: '1654'
ht-degree: 0%

---

# Web Application Firewall (WAF) powered by Fastly: die FAQ

## Wie funktioniert Adobe Commerce Managed Cloud WAF (powered by Fastly)?

Web Application Firewalls (WAFs) verhindern, [&#x200B; bösartiger Traffic &#x200B;](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) Websites und Netzwerken gelangt, indem sie den Traffic nach einer Reihe von Sicherheitsregeln filtern. Traffic, der Trigger einer der Regeln ist, wird blockiert, bevor er Ihre Websites oder Ihr Netzwerk beschädigen kann.

Adobe Commerce Cloud WAF bietet eine WAF-Richtlinie mit einem Regelsatz, der Ihre Adobe Commerce-Web-Anwendungen vor einer Vielzahl von Angriffen schützt.

Die WAF untersucht den Web- und Admin-Traffic, um verdächtige Aktivitäten zu identifizieren. Sie bewertet den GET und den POST-Traffic (HTTP-API-Aufrufe) und wendet den Regelsatz an, um zu bestimmen, welcher Traffic blockiert werden soll. Die WAF kann eine Vielzahl von Angriffen blockieren, darunter SQL Injection-Angriffe, Cross-Site-Scripting-Angriffe, Angriffe auf die Datenexfiltration und Verstöße gegen das HTTP-Protokoll.

Als Cloud-basierter Service benötigt WAF keine Hardware oder Software zur Installation oder Wartung. Fastly, ein bestehender Technologiepartner, bietet die Software und das Know-how. Ihre leistungsstarke, stets aktive WAF befindet sich in jedem Cache-Knoten im globalen Fastly-Bereitstellungsnetzwerk.

## Ist die WAF für alle Cloud-Kunden verfügbar?

Ja, der Cloud-WAF-Service ist ohne zusätzliche Kosten in Ihrem Adobe Commerce-Abonnement für die Cloud-Infrastruktur für die Architekturpläne Adobe Commerce on Cloud Infrastructure Starter und Adobe Commerce on Cloud Infrastructure Pro enthalten. Der WAF-Service ist in Produktions- und Staging-Umgebungen verfügbar.

## Erfüllt WAF die Anforderungen von PCI DSS 6.6?

Ja.

## Wenn mein Adobe Commerce in einem Cloud-Infrastrukturkonto Sites auf mehreren Domains verwaltet, ist das WAF-Profil dann auf jede Domain oder auf alle Domains abgestimmt?

Der WAF wird unter einem einzigen Cloud-Konto für alle Domains gemeinsam optimiert.

## Welche Regeln werden für die WAF verwendet?

Der Regelsatz im WAF-Profil, der auf Ihre Adobe Commerce in der Cloud-Infrastruktur-Produktionsumgebung angewendet wird, basiert auf dem Regelsatz OWASP Top 10 Threat Protection , der gängige Exploits für Web-Services abdeckt. Es enthält auch Adobe Commerce-spezifische Regeln, die von TrustWave SpiderLabs entwickelt wurden. Das Sicherheitsforschungsteam von Fastly hat auch Regeln hinzugefügt, die Ihre Website und Ihr Netzwerk vor allgemein bekannten Angriffen schützen: schlechte IP-Adressen, schlechte Benutzeragenten und bekannte Bot-Netz-Befehls- und Kontrollknoten. Wir aktivieren Regeln auf OWASP Paranoia Level 3 oder weniger, die eine hohe Sicherheitsabdeckung bieten.

## Wie greife ich auf Protokolle zu?

Um die Protokolle an Ihr Protokollierungs-Tool senden zu lassen, wenden Sie sich bitte an Ihren Technical Account Manager (TAM), um einen Protokollierungs-Endpunkt in Fastly hinzuzufügen.

## Wie sieht eine Blockanfrage aus?

Eine blockierte Anfrage gibt eine 403-Seite mit einer Anforderungskennung zurück.

Sie können diese Seite anpassen, solange die Anpassung die Anforderungskennung enthält. Weitere Informationen erhalten Sie von Ihrem technischen Kundenbetreuer.

## Wie aktualisieren wir WAF-Regelsätze? Wie schnell kann eine WAF-Regel geändert oder aktualisiert und global in der Produktion angewendet werden?

Als Teil des Cloud-WAF-Services verwaltet Fastly Regelaktualisierungen von kommerziellen Drittanbietern, Fastly Research und Open Sources. Sie aktualisieren veröffentlichte Regeln nach Bedarf oder wenn Änderungen an den Regeln aus ihren jeweiligen Quellen verfügbar sind in eine Richtlinie. Neue Regeln, die mit den veröffentlichten Regelklassen übereinstimmen, werden ebenfalls in die WAF-Instanz eines beliebigen Services eingefügt, sobald sie aktiviert ist. Dies hilft, eine sofortige Abdeckung für neue oder sich entwickelnde Exploits sicherzustellen. Informationen ([&#x200B; zu Regelaktualisierungen und Wartungsarbeiten) &#x200B;](https://docs.fastly.com/guides/web-application-firewall/fastly-waf-rule-set-updates-maintenance#rule-set-maintenance) Sie auf der Dokumentations-Site von Fastly.

## Wie unterscheidet sich Adobe Commerces Cloud-WAF von der WAF-Lösung, die Fastly seinen Direktkunden anbietet?

Die WAF-Lösung, die direkt von Fastly verkauft wird, ist ein kostenpflichtiges Angebot, das umfassendere Regelsätze und zusätzliche Funktionen wie Regelanpassung und Malware-Schutz umfasst. Die Cloud-WAF-Lösung von Adobe Commerce umfasst eine Untergruppe von Regeln, die auf das Adobe Commerce-Programm abzielen, und enthält nur einen Regelsatz für die Produktionsumgebung jedes Kunden.

## Vor welchen Arten von Sicherheitsbedrohungen schützt WAF?

<table class="table-basic" style="width: 649px;">
<tbody>
<tr>
<th style="width: 145.5px; text-align: left;">Drohung</th>
<th style="width: 497.5px; text-align: left;">WAF-Schutz</th>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">SQL Injection-Angriffe</td>
<td style="width: 497.5px;">Sowohl der OWASP ModSecurity Core Rule Set als auch der TrustWave Commercial Rule Set enthalten spezifische Filter für SQL Injection-Angriffe und deren Varianten.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">
<p>Cross-Site-Injektion</p>
</td>
<td style="width: 497.5px;">Der OWASP-Regelsatz schützt vor Cross-Site-Injection-Angriffen. nutzt schnell einen Bewertungsmechanismus für jede Anfrage und sucht nach einer standortübergreifenden Injektion und anderen Bedrohungen für den Ursprung. Wir bewerten jede Anfrage hinsichtlich des gesamten Kernregelsatzes und überprüfen, ob der Anfragewert unter einem konfigurierbaren Schwellenwert liegt, damit er erfolgreich ist.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Brute-Force-Angriffe</td>
<td style="width: 497.5px;">Wird vom OWASP-Regelsatz abgedeckt. Fastly blockiert auch Brute-Force-Aktivitäten, indem VCL-Code verwendet wird, der bestimmte Quellen, Anfragen oder Versuche erkennt, Sicherheitskontrollen zu überfordern oder zu überfordern, bevor Traffic das ursprüngliche Rechenzentrum erreicht.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Netzwerkangriffe</td>
<td style="width: 497.5px;">Netzwerkangriffe oder Angriffe auf Netzwerkinfrastrukturen werden automatisch von Fastly verwaltet. Fastly übergibt kein DNS an den Ursprung, und Traffic, der nicht mit einem engen HTTP-, HTTPS- oder DNS-Profil übereinstimmt, wird am Rand des Netzwerks verworfen. Angriffe auf Steuerungsprotokolle werden durch die Authentifizierung von Endpunkten im gesamten Netzwerk abgewehrt. Zusätzlich werden die im Fastly-Netzwerk verwendeten Netzwerkprotokolle gehärtet, um sicherzustellen, dass sie nicht als Verstärkungs- oder Reflexionsmittel genutzt werden können. Kunden sind dafür verantwortlich, sich vor Angriffen zu schützen, die das Fastly-Netzwerk umgehen, indem sie den IP-Adressbereich von Fastly Cache nutzen, der unseren Kunden als Komponente unseres CDN-Service veröffentlicht wird. Es wird empfohlen, den ursprünglichen IP-Adressbereich nicht im öffentlichen DNS zu veröffentlichen, um sicherzustellen, dass Bypass-Angriffe diese Adressen nicht als Ziele verwenden können.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">JavaScript Injection-Angriffe</td>
<td style="width: 497.5px;">WAF-Regeln schützen vor bösartigem JavaScript-Code, der in die Clientkommunikation mit Webservices eingefügt wird. Häufige Exploit-Muster oder -Bewertungen werden über die WAF gefiltert, um die Integrität des Ursprungs-Service sicherzustellen.</td>
</tr>
</tbody>
</table>

## Werden zusätzliche Funktionen angeboten?

Adobe Commerces WAF-Angebot umfasst Schutz vor den Top-10-Bedrohungen von OWASP im Rahmen der PCI-Anforderungen, 24x7-Unterstützung, einschließlich Triage für falsch positive Ergebnisse und Versionsaktualisierungen. Die folgenden Funktionen werden im Standardangebot nicht unterstützt:

* Ratenbegrenzung
* Regelanpassungen
* Bot-Abmilderung
* Malware-Schutz

## Wie wirkt sich die WAF auf die Leistung meiner Site aus?

Für jede nicht zwischengespeicherte Anfrage wird eine geschätzte Latenz von 1,5 Millisekunden (ms) bis 20 ms eingeführt.

## Können Kunden IP-Blacklists erstellen und ändern, um den Traffic zu blockieren?

Ja, Kunden können die Blockierung nach Land und Zugriffssteuerungsliste (ACL) über die Admin-Benutzeroberfläche von Adobe Commerce in der Cloud-Infrastruktur aktivieren. Verwenden Sie diese Funktionen in Fällen, in denen Sie den Zugriff für Besucher aus bestimmten Ländern oder bestimmten IP-Adressen oder IP-Bereichen blockieren möchten. Wenn Sie möchten, dass blockierte Besucherinnen und Besucher eine benutzerdefinierte Seite und keinen Fehlercode sehen, können Sie eine benutzerdefinierte Fehlerseite erstellen, indem Sie im Fastly-Konfigurationsmenü HTML hochladen. Siehe [Erstellen einer benutzerdefinierten Fehler-/Wartungsseite](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=de) in unserer Entwicklerdokumentation.

## Wo kann ich den Betriebsstatus meines WAF-Service überprüfen?

Die allgemeine Verfügbarkeit des WAF-Service wird auf der Seite [Fastly-Status](https://status.fastly.com/) gemeldet. Verfügbarkeitsberichte für die WAF einzelner Kundinnen und Kunden werden nicht bereitgestellt.

## Bietet Adobe Commerce Incident-Management für den WAF-Service?

Derzeit wird kein Incident-Management angeboten.

## Verfügt Adobe Commerce über ein Sicherheitszentrum?

Obwohl Adobe Commerce nicht über ein Sicherheitsbetriebszentrum verfügt, verfügen wir über einen Prozess für Sicherheitsoperationen, der es uns ermöglicht, die richtigen Ressourcen einzusetzen, um in Echtzeit auf Sicherheitsvorfälle zu reagieren. Wir bieten auch 24/7/365 Follow-the-Sun-Support.

Sie können auch Adobe Commerce-bezogene Sicherheitsnachrichten und -aktualisierungen vom [Sicherheitscenter](https://helpx.adobe.com/de/security.html) erhalten.

## Welche Unterstützung ist verfügbar?

Der WAF-Support bietet die folgenden Ressourcen, um die Auswirkungen unerwünschter oder böswilliger Anfragen auf den Service zu minimieren:

* Onboarding: Aktivierung, Ersteinrichtung und begrenzte Überwachung der Fastly-Services, die die Adobe Commerce Managed Cloud WAF unterstützen
* Laufende falsch-positive Analyse zur Behandlung von Instanzen, in denen der WAF legitimen Traffic blockiert
* Konfiguration aller neuen Standardregeln, die im Rahmen von WAF-Versionsaktualisierungen eingeführt werden

Weitere Support[Informationen, einschließlich Schweregraden, Antwortzeiten, Kanälen und Verfügbarkeit, finden Sie in den &#x200B;](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Magento-Support-Services-Terms-and-Conditions.pdf) von Cloud SLA.

## Wie erhalte ich Hilfe, wenn WAF legitimen Traffic blockiert oder andere Probleme verursacht?

[Senden eines Support-Tickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) im [Adobe Commerce Help Center](https://support.magento.com). Bitte geben Sie an, dass das Ticket mit dem WAF-Service verbunden ist, und geben Sie die Kennung (ID) der blockierten Anfrage an.

Das Support-Ticketing-System von Adobe Commerce verfolgt die Kommunikation zwischen unseren Support-Technikern und den Mitarbeitern des Kunden. Dieses System stellt ein Protokoll der Kommunikation mit Zeitstempel bereit und sendet E-Mails an die Mitarbeiter von Kunden und Adobe Commerce, wenn Tickets aktualisiert werden.

Bei allen Online-Vorfällen wird der Eingang der Vorfälle über das Ticketing-System des Adobe Commerce-Kundenhilfezentrums bestätigt. Nach Eingang eines ordnungsgemäß übermittelten Vorfalls werden die Unterstützungsdienste gemäß den oben dargelegten Prioritätsstufen priorisiert.

In der folgenden Tabelle sind die Support-Kanäle und die Verfügbarkeit von WAF-Support zusammengefasst:

<table class="table-basic">
<tbody>
<tr>
<th>Support-Angebot</th>
<th>Details</th>
</tr>
<tr>
<td>Online-Selbsthilfe</td>
<td>Uneingeschränkter Zugriff</td>
</tr>
<tr>
<td>Verfügbarkeit von Berichten zu Vorfällen</td>
<td>24/7</td>
</tr>
<tr>
<td>Web-Portal</td>
<td>Verfügbar über Zendesk</td>
</tr>
<tr>
<td>Notfall-Eskalation*</td>
<td>Siehe <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/adobe-commerce-p1-notification-hotline.html?lang=de">Adobe Commerce P1-Benachrichtigungs-Hotline</a>-Artikel für US- und internationale Nummern.</td>
</tr>
</tbody>
</table>

*\* Die gebührenfreie Telefonleitung von Adobe Commerce ist nur für Vorfälle der Priorität 1 reserviert. Nicht-Prioritäts-1-Aufrufe verlangsamen die Reaktion auf Probleme insgesamt*

## Wie werden falsch-positive Ergebnisse bewertet?

Wir haben einen falsch-positiven Triage-Prozess (24x7 verfügbar), um Instanzen schnell zu beheben und zu beheben, bei denen legitime Anfragen eine WAF-Regel ausgelöst haben. Falsch-positive Ereignisse werden als Probleme der Priorität 1 behandelt. Standardmäßig kann unser Support-Team die WAF-Richtlinie sofort aktualisieren, um die Regel zu deaktivieren, die das Blockierungsereignis ausgelöst hat, und der legitimen Anfrage zu erlauben, den WAF zu durchlaufen.

## Was passiert, wenn der Traffic zum Administratorbereich der Adobe Commerce auf der Website der Cloud-Infrastruktur WAF-Regeln für Trigger angibt? Kann der Adobe Commerce-Support Probleme mit blockiertem Admin-Traffic beheben?

Ja, blockierter Admin-Traffic wird als Problem der Priorität 1 behandelt.
