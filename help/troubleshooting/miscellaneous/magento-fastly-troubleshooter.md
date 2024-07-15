---
title: Adobe Commerce - Schnellere Fehlerbehebung
description: Diese schnelle Problembehebung für Adobe Commerce-Benutzer führt Sie zu den Lösungen, basierend auf Ihrer Antwort auf die angezeigten Symptome. Klicken Sie auf die Fragen, um die nächsten Optionen oder Antworten anzuzeigen.
exl-id: c5c51b89-5a7d-49ba-a0ee-7abbaf78fdad
feature: Support, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# Adobe Commerce - Schnellere Fehlerbehebung

Diese schnelle Problembehebung für Adobe Commerce-Benutzer führt Sie zu den Lösungen, basierend auf Ihrer Antwort auf die angezeigten Symptome. Klicken Sie auf die Fragen, um die nächsten Optionen oder Antworten anzuzeigen.

## Schritt 1: Überprüfen des Schnelldienstes {#step-1}

+++**Der Kunde meldet ein Problem mit Fastly. Ist der Fastly-Dienst ausgefallen?**

a. YES - Aktivieren Sie [Fastly Service Status](https://status.fastly.com/) und senden Sie ein Adobe Commerce-Supportticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).[\
b. NO - Fahren Sie mit [Schritt 2](#step-2) fort.

+++

## Schritt 2: Überprüfen der VCL-Konfigurationsdatei {#step-2}

+++**Haben Sie Fehler, wenn Sie Backend-Tester ausführen?**

Führen Sie Ihre Projekt-URL über den [Backend-Tester - Fastly](https://magento-tester.global.ssl.fastly.net/magento-tester/) aus. Es zeigt die Version der VCL-Konfigurationsdatei, wenn die Seite zwischenspeicherbar ist, die Version des Fastly-Moduls und andere nützliche Informationen zur Fehlerbehebung. Hast du Fehler?

a. YES - Sie haben die Meldung _Plugin VCL Version ist veraltet! Bitte neu hochladen._ Die Lösung für diesen Fehler finden Sie unter [Fastly Error: Plugin VCL Version ist veraltet! Laden Sie ](/help/troubleshooting/miscellaneous/fastly-error-plugin-vcl-version-is-outdated-please-re-upload.md) erneut hoch.\
b. NO - [Schritt 3](#step-3).

+++

## Schritt 3: Auf Fehler bei der Bildoptimierung prüfen {#step-3}

+++**Bildoptimierungsfehler?**

a. YES - [Fehler bei der Aktivierung der Bildoptimierung](/help/troubleshooting/miscellaneous/error-enabling-image-optimization-in-magento-commerce.md).\
b. NO - Überprüfen Sie das DNS, indem Sie im CLI/Terminal ausgeführt werden: `dig [your website.com] + short`. Fahren Sie mit [Schritt 4](#step-4) fort.

+++

## Schritt 4: DNS überprüfen {#step-4}

+++**Was passiert, wenn Sie `dig` ausführen?**

Wenn Sie `dig` ausgeführt haben, wurde ein Datensatz zurückgegeben, der auf prod.magentocloud.map.fastly.net oder eine der folgenden IP-Adressen verweist (siehe [Aktualisieren der DNS-Konfiguration mit der Produktionseinstellung](https://devdocs.magento.com/cloud/live/site-launch-checklist.html#dns) in unserer Entwicklerdokumentation):

* 151 101 1 124
* 151 101 65 124
* 151 101 129 124
* 151 101 193 124

a. YES - Das Problem ist nicht DNS-bezogen. Fahren Sie mit [Schritt 5](#step-5) fort.\
b. NO - Das Problem ist wahrscheinlich DNS-bezogen. Der Kunde sollte [die DNS-Konfiguration überprüfen](https://devdocs.magento.com/cloud/live/site-launch-checklist.html#dns "https://devdocs.magento.com/cloud/live/site-launch-checklist.html#dns") oder sich an seinen DNS-Provider wenden, um weitere Informationen zu erhalten.

+++

## Schritt 5: Verbindung bestätigen {#step-5}

+++**Erhalten Sie eine Meldung &quot;Verbindung unsicher&quot;oder &quot;Nicht sicher&quot;, die bei Ausführung von `curl -svo /dev/null "https://website.com"` im CLI/Terminal zurückgegeben wird?**

a. YES - Dies ist wahrscheinlich ein Zertifikatproblem. Rufen Sie die Website in einem Browser auf, wählen Sie das Sperrsymbol aus und suchen Sie nach einem Zertifikatablauf. Fahren Sie mit [Schritt 6](#step-6) fort.\
b. NO - Besuchen Sie [http://fastly-debug.com](https://www.fastly-debug.com/) und geben Sie diese Informationen in einem [Adobe Commerce-Supportticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) frei.

+++

## Schritt 6: Bestätigen, dass Sie über ein gültiges TSL-Zertifikat verfügen {#step-6}

+++**Ist das Zertifikat abgelaufen?**

a. YES - Sie müssen Ihr TLS-Zertifikat bei der Zertifizierungsstelle (Certificate Authority, CA) erneuern.\
b. NO - Sie dürfen kein Zertifikat haben. Wenn Sie über Adobe Commerce verfügen, empfehlen wir Ihnen, ein TLS-Zertifikat zu erwerben. Wenn Sie sich auf Adobe Commerce in der Cloud-Infrastruktur befinden, können Sie über ein domänenvalidiertes Zertifikat verfügen, das SSL-/TLS-Verschlüsselungszertifikat verwenden soll, um sicheren HTTPS-Traffic von Fastly aus bereitzustellen. Siehe [Bereitstellen von SSL-/TLS-Zertifikaten](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#provision-ssltls-certificates) in unserer Entwicklerdokumentation.

+++

[Zurück zu Schritt 1](#step-1)
