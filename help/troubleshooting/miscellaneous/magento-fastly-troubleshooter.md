---
title: Adobe Commerce Fastly-Fehlerbehebung
description: Dieser Fastly-Ratgeber für Adobe Commerce-Anwender führt Sie anhand Ihrer Reaktion auf die Symptome zu den Lösungen. Klicken Sie auf die Fragen, um die nächsten Optionen oder Antworten anzuzeigen.
exl-id: c5c51b89-5a7d-49ba-a0ee-7abbaf78fdad
feature: Support, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Adobe Commerce Fastly-Fehlerbehebung

Dieser Fastly-Ratgeber für Adobe Commerce-Anwender führt Sie anhand Ihrer Reaktion auf die Symptome zu den Lösungen. Klicken Sie auf die Fragen, um die nächsten Optionen oder Antworten anzuzeigen.

## Schritt 1: Fastly-Service überprüfen {#step-1}

+++**Der Kunde meldet ein Problem mit Fastly. Ist der Fastly-Service nicht verfügbar?**

a. JA - Überprüfen Sie [Fastly Service Status](https://status.fastly.com/) und [senden Sie ein Adobe Commerce Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NEIN - Mit [Schritt 2](#step-2) fortfahren.

+++

## Schritt 2: Überprüfen der VCL-Konfigurationsdatei {#step-2}

+++**Haben Sie Fehler, wenn Sie Backend Tester ausführen?**

Führen Sie Ihre Projekt-URL über den [Backend-Tester - Fastly](https://magento-tester.global.ssl.fastly.net/magento-tester/) aus. Es zeigt die Version der VCL-Konfigurationsdatei, wenn die Seite zwischenspeicherbar ist, die Version des Fastly-Moduls und andere nützliche Fehlerbehebungsinformationen. Haben Sie Fehler?

a. JA - Sie haben die Nachricht _Plugin VCL Version ist veraltet! Bitte erneut hochladen._ Die Lösung für diesen Fehler finden Sie unter [Fastly Error: Plugin VCL Version ist veraltet! Bitte erneut hochladen](/help/troubleshooting/miscellaneous/fastly-error-plugin-vcl-version-is-outdated-please-re-upload.md).\
b. NEIN - [Schritt 3](#step-3).

+++

## Schritt 3: Prüfen auf Fehler bei der Bildoptimierung {#step-3}

+++**Fehler bei der Bildoptimierung?**

a. JA - [Fehler bei Aktivierung der &#x200B;](/help/troubleshooting/miscellaneous/error-enabling-image-optimization-in-magento-commerce.md))\
b. NEIN - Überprüfen Sie das DNS, indem Sie in der CLI/im Terminal ausführen: `dig [your website.com] + short`. Fahren Sie mit [Schritt 4](#step-4) fort.

+++

## Schritt 4: Überprüfen des DNS {#step-4}

+++**Was passiert, wenn man `dig` läuft?**

Wenn Sie `dig` ausgeführt haben, wurde ein Datensatz zurückgegeben, der auf prod.magentocloud.map.fastly.net oder eine der folgenden IP-Adressen verweist (siehe [Aktualisieren der DNS-Konfiguration mit Produktionseinstellungen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/launch/checklist#update-dns-configuration-with-production-settings) in unserer Entwicklerdokumentation):

* 151.101.1.124
* 151.101.65.124
* 151.101.129.124
* 151.101.193.124

a. JA - Das Problem ist nicht DNS-bezogen. Fahren Sie mit [Schritt 5](#step-5) fort.\
b. NEIN - Das Problem ist wahrscheinlich DNS-bezogen. Der Kunde sollte [DNS-Konfiguration überprüfen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/launch/checklist#update-dns-configuration-with-production-settings) oder seinen DNS-Anbieter kontaktieren, um weitere Informationen zu erhalten.

+++

## Schritt 5: Bestätigen der Verbindung {#step-5}

+++**Wird bei der Ausführung von `curl -svo /dev/null "https://website.com"` im CLI/Terminal die Meldung „Verbindung unsicher“ oder „Nicht sicher“ zurückgegeben?**

a. JA - Dies ist wahrscheinlich ein Zertifikatsproblem. Besuchen Sie die Website in einem Browser, klicken Sie auf das Sperrsymbol und suchen Sie nach einem Gültigkeitsablauf des Zertifikats. Fahren Sie mit [Schritt 6](#step-6) fort.\
b. NEIN - Besuchen Sie [http://fastly-debug.com](https://www.fastly-debug.com/) und geben Sie diese Informationen in einem [Adobe Commerce-Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) weiter.

+++

## Schritt 6: Bestätigen Sie, dass Sie über ein gültiges TSL-Zertifikat verfügen {#step-6}

+++**Ist das Zertifikat abgelaufen?**

a. JA - Sie müssen Ihr TLS-Zertifikat bei der Zertifizierungsstelle (CA) erneuern.\
b. NEIN - Sie haben möglicherweise gar kein Zertifikat. Wenn Sie über Adobe Commerce verfügen, empfehlen wir Ihnen, ein TLS-Zertifikat zu erwerben. Wenn Sie sich in der Cloud-Infrastruktur von Adobe Commerce befinden, können Sie ein von der Domain validiertes SSL/TLS-Zertifikat verschlüsseln lassen, um sicheren HTTPS-Traffic von Fastly bereitzustellen. Siehe [Bereitstellen von SSL-/TLS-](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates)) in unserer Entwicklerdokumentation.

+++

[Zurück zu Schritt 1](#step-1)
