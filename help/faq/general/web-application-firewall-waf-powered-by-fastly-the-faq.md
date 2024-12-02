---
title: 'Web Application Firewall (WAF), powered by Fastly: FAQ'
description: Web Application Firewalls (WAFs) verhindern, dass böswilliger Traffic auf Websites und in Netzwerken zugreift, indem der Traffic nach einer Reihe von Sicherheitsregeln gefiltert wird. Der Traffic, der von Triggern auf Regeln angewendet wird, wird blockiert, bevor er Ihre Sites oder Ihr Netzwerk beschädigen kann.
exl-id: d977ea68-7d8c-4863-b026-acdc25d8c430
feature: Cache
source-git-commit: f384ff9d5d8a8c5c5da20b582c02a2d783b32d7e
workflow-type: tm+mt
source-wordcount: '1654'
ht-degree: 0%

---

# Web Application Firewall (WAF), powered by Fastly: FAQ

## Wie funktioniert die Managed Cloud WAF von Adobe Commerce (powered by Fastly)?

Web Application Firewalls (WAFs) verhindern, dass [bösartiger Traffic](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) auf Sites und Netzwerke zugreift, indem der Traffic nach einer Reihe von Sicherheitsregeln gefiltert wird. Der Traffic, der von Triggern auf Regeln angewendet wird, wird blockiert, bevor er Ihre Sites oder Ihr Netzwerk beschädigen kann.

Adobe Commerce Cloud WAF bietet eine WAF-Richtlinie mit einem Regelsatz, der Ihre Adobe Commerce-Webanwendungen vor einer Vielzahl von Angriffen schützt.

Die WAF untersucht den Web- und Admin-Traffic, um verdächtige Aktivitäten zu identifizieren. Sie wertet den GET- und den POST-Traffic (HTTP-API-Aufrufe) aus und wendet den Regelsatz an, um zu bestimmen, welcher Traffic blockiert werden soll. Die WAF kann eine Vielzahl von Angriffen verhindern, darunter SQL-Injection-Angriffe, Cross-Site-Scripting-Angriffe, Angriffe auf Datenexfiltration und HTTP-Protokollverletzungen.

Als Cloud-basierter Dienst benötigt die WAF keine Hardware oder Software, um sie zu installieren oder zu warten. Fastly, ein bestehender Technologiepartner, bietet die Software und das Know-how. Ihr leistungsstarkes, stets On-WAF-System befindet sich in jedem Cache-Knoten im globalen Bereitstellungsnetzwerk von Fastly.

## Ist die WAF für alle Cloud-Kunden verfügbar?

Ja, der Cloud WAF-Dienst ist in Ihrer Adobe Commerce im Rahmen eines Cloud-Infrastrukturabonnements für Adobe Commerce in der Starter-Planarchitektur für Cloud-Infrastruktur und Adobe Commerce in der Planarchitektur von Cloud Infrastructure Pro ohne zusätzliche Kosten enthalten. Der WAF-Dienst ist in Produktions- und Staging-Umgebungen verfügbar.

## Entspricht WAF den PCI DSS 6.6-Anforderungen?

Ja.

## Wenn mein Adobe Commerce-Konto für die Cloud-Infrastruktur Sites auf mehreren Domänen verwaltet, wird das WAF-Profil für jede Domäne oder kollektiv für alle Domänen optimiert?

Die WAF wird für alle Domänen unter einem einzigen Cloud-Konto gemeinsam optimiert.

## Welche Regeln werden für die WAF verwendet?

Der Regelsatz im WAF-Profil, der auf Ihre Adobe Commerce in der Produktionsumgebung der Cloud-Infrastruktur angewendet wird, basiert auf dem Regelsatz OWASP Top 10 für den Schutz von Bedrohungen durch übertragbare Krankheiten, der häufige Exploits bei Webdiensten abdeckt. Es enthält auch Adobe Commerce-spezifische Regeln, die von TrustWave SpiderLabs entwickelt wurden. Das Sicherheits-Forschungsteam von Fastly hat außerdem Regeln hinzugefügt, die Ihre Website und Ihr Netzwerk vor allgemein bekannten Angriffen schützen: schlechte IP-Adressen, schlechte Benutzeragenten und bekannte Bot-Befehle und Kontrollknoten. Wir ermöglichen Regeln auf OWASP Paranoia Level 3 oder weniger, die eine hohe Sicherheit bieten.

## Wie greife ich auf Protokolle zu?

Um die Protokolle an Ihr Protokollierungstool zu senden, wenden Sie sich an Ihren technischen Kundenbetreuer (TAM), um in Fastly einen Protokollierungsendpunkt hinzuzufügen.

## Wie sieht eine Blockanfrage aus?

Eine blockierte Anfrage gibt eine 403-Seite mit einer Anforderungskennung zurück.

Sie können diese Seite anpassen, solange die Anpassung die Anforderungskennung enthält. Weitere Informationen erhalten Sie von Ihrem technischen Kundenbetreuer.

## Wie aktualisieren wir WAF-Regelsätze? Wie schnell kann eine WAF-Regel in der Produktion geändert oder aktualisiert und global angewendet werden?

Als Teil des Cloud WAF-Dienstes verwaltet Fastly Regelaktualisierungen von kommerziellen Dritten, schnelle Forschung und Open Source. Sie aktualisieren veröffentlichte Regeln bei Bedarf oder wenn Änderungen an den Regeln aus den entsprechenden Quellen verfügbar sind, in einer Richtlinie. Neue Regeln, die mit den veröffentlichten Regelklassen übereinstimmen, werden nach der Aktivierung auch in die WAF-Instanz eines Dienstes eingefügt. Dadurch wird eine sofortige Abdeckung neuer oder sich entwickelnder Exploits sichergestellt. Sie können Informationen [ über Regelaktualisierungen und -wartung](https://docs.fastly.com/guides/web-application-firewall/fastly-waf-rule-set-updates-maintenance#rule-set-maintenance) auf der Schnelldokumentations-Site lesen.

## Inwiefern unterscheidet sich die Cloud WAF von der WAF-Lösung Fastly für Direktkunden?

Die WAF-Lösung, die direkt von Fastly verkauft wird, ist ein kostenpflichtiges Angebot, das breitere Regelsätze und zusätzliche Funktionen wie Regelanpassung und Malware-Schutz umfasst. Die Cloud WAF-Lösung von Adobe Commerce umfasst einen Teil der Regeln, die auf die Adobe Commerce-Anwendung ausgerichtet sind, und enthält nur einen Regelsatz für die Produktionsumgebung jedes Kunden.

## Vor welchen Sicherheitsbedrohungen schützt WAF?

<table class="table-basic" style="width: 649px;">
<tbody>
<tr>
<th style="width: 145.5px; text-align: left;">Bedrohung</th>
<th style="width: 497.5px; text-align: left;">WAF-Schutz</th>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">SQL-Injection-Angriffe</td>
<td style="width: 497.5px;">Sowohl der OWASP ModSecurity-Core-Regelsatz als auch der TrustWave-kommerzielle Regelsatz enthalten spezifische Filter für SQL-Injection-Angriffe und deren Varianten.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">
<p>Injektionsstelle</p>
</td>
<td style="width: 497.5px;">Der OWASP-Regelsatz schützt vor Cross-Site-Injection-Angriffen. Nutzt schnell einen Scoring-Mechanismus für jede Anfrage, die nach einer Website-übergreifenden Injektion sucht, und andere Bedrohungen für den Ursprung. Wir bewerten jede Anforderung mit dem gesamten Kernregelsatz und überprüfen, ob der Anforderungswert unter einem konfigurierbaren Schwellenwert liegt, damit er erfolgreich ist.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Brutto-Force-Angriffe</td>
<td style="width: 497.5px;">Wird durch den OWASP-Regelsatz abgedeckt. Blockiert auch die Brute-Force-Aktivität mithilfe von VCL-Code, der bestimmte Quellen, Anforderungen oder Versuche erkennt, die Sicherheitskontrollen zu erzwingen oder zu überwältigen, bevor der Traffic das Ursprungs-Datenzentrum erreicht.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Netzwerkangriffe</td>
<td style="width: 497.5px;">Netzwerkangriffe oder Angriffe, die auf eine Netzwerkinfrastruktur abzielen, werden automatisch von Fastly verwaltet. DNS wird schnell nicht an den Ursprung übergeben und Traffic, der nicht mit einem schmalen HTTP-, HTTPS- oder DNS-Profil übereinstimmt, wird am Netzwerkrand verworfen. Angriffe auf Zielgruppen-Kontrollprotokolle werden durch Authentifizierung von Endpunkten im gesamten Netzwerk abgewehrt. Darüber hinaus werden die im Fastly-Netzwerk verwendeten Netzwerkprotokolle gehärtet, um sicherzustellen, dass sie nicht als Mittel zur Verstärkung oder Reflexion genutzt werden können. Kunden sind für den Schutz vor Angriffen verantwortlich, die das Fastly-Netzwerk umgehen, indem sie den für unsere Kunden als Bestandteil unseres CDN-Dienstes veröffentlichten IP-Adressraum Fastly Cache nutzen. Es wird empfohlen, den IP-Adressenraum des Ursprungs nicht im öffentlichen DNS zu veröffentlichen, um sicherzustellen, dass Bypass-Angriffe diese Adressen nicht als Ziele verwenden können.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">JavaScript-Injektionsangriffe</td>
<td style="width: 497.5px;">WAF-Regeln schützen vor schädlichem JavaScript-Code, der in die Clientkommunikation mit Webdiensten eingefügt wird. Allgemeine Exploit-Muster oder -Werte werden durch die WAF gefiltert, um die Integrität des Ursprungs-Service sicherzustellen.</td>
</tr>
</tbody>
</table>

## Sind zusätzliche Funktionen verfügbar?

Das WAF-Angebot von Adobe Commerce umfasst den Schutz vor OWASP Top-10-Bedrohungen im Rahmen von PCI-Anforderungen, rund um die Uhr verfügbare Unterstützung, einschließlich Testen auf Falsch-Positiv-Werte und Versionsaktualisierungen. Die folgenden Funktionen werden im Standardangebot nicht unterstützt:

* Ratenbegrenzung
* Regelanpassungen
* Bot-Abschwächung
* Malware-Schutz

## Wie wirkt sich die WAF auf meine Site-Leistung aus?

Für jede nicht zwischengespeicherte Anforderung wird eine geschätzte Latenz von 1,5 Millisekunden (ms) bis 20 ms eingeführt.

## Können Kunden IP-Blacklists erstellen und ändern, um Traffic zu blockieren?

Ja, Kunden können über die Admin-Benutzeroberfläche der Cloud-Infrastruktur die Blockierung nach Land und Zugriffssteuerungsliste (ACL) aus der Adobe Commerce aktivieren. Verwenden Sie diese Funktionen in Fällen, in denen Sie den Zugriff für Besucher aus bestimmten Ländern oder bestimmten IP-Adressen oder IP-Bereichen blockieren möchten. Wenn blockierte Besucher eine benutzerdefinierte Seite anstelle eines Fehlercodes sehen sollen, können Sie eine benutzerdefinierte Fehlerseite erstellen, indem Sie HTML im Menü Schnelle Konfiguration hochladen. Siehe [Erstellen einer benutzerdefinierten Fehler-/Wartungsseite](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) in unserer Entwicklerdokumentation.

## Wo kann ich den Betriebsstatus meines WAF-Dienstes überprüfen?

Die Gesamtverfügbarkeit des WAF-Dienstes wird auf der Seite [Schneller Status](https://status.fastly.com/) gemeldet. Verfügbarkeitsberichte für die WAF einzelner Kunden werden nicht bereitgestellt.

## Bietet Adobe Commerce Incident Management für den WAF-Dienst?

Derzeit ist das Incident Management nicht verfügbar.

## Verfügt Adobe Commerce über ein Sicherheitszentrum?

Adobe Commerce verfügt zwar nicht über ein Sicherheitszentrum, aber wir verfügen über einen Sicherheitsprozess, der es uns ermöglicht, die richtigen Ressourcen bereitzustellen, um auf Sicherheitsvorfälle in Echtzeit zu reagieren. Wir bieten auch 24/7/365 Follow-the-sun Support.

Außerdem erhalten Sie vom [Sicherheitszentrum](https://helpx.adobe.com/security.html) Sicherheitsaktualisierungen zu Adobe Commerce-bezogenen Sicherheitsnachrichten.

## Welche Unterstützung ist verfügbar?

Der WAF-Support bietet die folgenden Ressourcen, die Sie bei der Reduzierung der Service-Auswirkungen unerwünschter oder böswilliger Anfragen unterstützen:

* Onboarding: Aktivierung, Ersteinrichtung und eingeschränkte Überwachung der Fastly-Dienste, die die Adobe Commerce Managed Cloud WAF unterstützen
* Laufende Fehlversuche mit positivem Verlauf zur Behandlung von Fällen, in denen der WAF legitimen Traffic blockiert
* Konfiguration aller neuen Standardregeln, die im Rahmen von WAF-Versionsaktualisierungen eingeführt wurden

Weitere Informationen zu Support-Informationen, einschließlich Schweregrad-Definitionen, Antwortzeiten, Kanälen und Verfügbarkeit, finden Sie in den [Cloud SLA](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Magento-Support-Services-Terms-and-Conditions.pdf) -Begriffen.

## Wenn die WAF legitimen Traffic blockiert oder andere Probleme verursacht, wie erhalte ich dann Hilfe?

[Senden Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) im [Adobe Commerce Help Center](https://support.magento.com). Bitte geben Sie an, dass das Ticket mit dem WAF-Dienst verbunden ist, und geben Sie die Kennung der blockierten Anfrage (ID) an.

Das Adobe Commerce Support-Ticketingsystem verfolgt die Kommunikation zwischen unseren Support-Mitarbeitern und den Mitarbeitern eines Kunden. Dieses System bietet ein zeitgestempeltes Transkript von Nachrichten und sendet E-Mails an Kunden und Mitarbeiter von Adobe Commerce, sobald die Tickets aktualisiert werden.

Bei allen online eingereichten Vorfällen wird der Eingang von Vorfällen über das Ticketingsystem des Adobe Commerce-Kundenunterstützungszentrums bestätigt. Bei Eingang eines ordnungsgemäß übermittelten Vorfalls werden die Unterstützungsdienste entsprechend den oben genannten Prioritätsstufen priorisiert.

Die folgende Tabelle fasst die Supportkanäle und die Verfügbarkeit für den WAF-Support zusammen:

<table class="table-basic">
<tbody>
<tr>
<th>Support-Angebot</th>
<th>Details</th>
</tr>
<tr>
<td>Online-Selbsthilfe</td>
<td>Unbegrenzter Zugriff</td>
</tr>
<tr>
<td>Verfügbarkeit von Berichten zu Vorfällen</td>
<td>07.24.2017</td>
</tr>
<tr>
<td>Webportal</td>
<td>Verfügbar über Zendesk</td>
</tr>
<tr>
<td>Notfalleskalierung*</td>
<td>Informationen zu US- und internationalen Nummern finden Sie im Artikel <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/adobe-commerce-p1-notification-hotline.html">Hotline für Benachrichtigungen über Adobe Commerce P1</a> .</td>
</tr>
</tbody>
</table>

*\* Die gebührenfreie Telefonleitung für den Support von Adobe Commerce ist nur für Vorfälle der Kategorie 1 reserviert. Aufrufe ohne Priorität 1 verlangsamen die Gesamtantwort auf Probleme*

## Wie werden falsch-positive Ergebnisse getestet?

Wir verfügen über einen falsch positiven Testprozess (rund um die Uhr verfügbar), um schnell auf Fälle zu reagieren und diese zu beheben, in denen berechtigte Anforderungen eine WAF-Regel ausgelöst haben. Falsch positive Ereignisse werden als Probleme der Priorität 1 behandelt. Als Standardaktion kann unser Support-Team die WAF-Richtlinie sofort aktualisieren, um die Regel zu deaktivieren, die das Blockierungsereignis ausgelöst hat, und es zu ermöglichen, dass die berechtigte Anfrage über die WAF weitergeleitet wird.

## Was passiert, wenn der Traffic zum Administratorbereich von Adobe Commerce auf den Site-Triggern der Cloud-Infrastruktur WAF-Regeln anwendet? Wird der Adobe Commerce-Support Probleme mit blockiertem Admin-Traffic lösen?

Ja, blockierter Admin-Traffic wird als Problem mit Priorität 1 behandelt.
