---
title: Auf Adobe Commerce in Cloud-Infrastruktur gestartete Blockierungen
description: Dieser Artikel enthält eine Fehlerbehebung für Blocker, die in Adobe Commerce in der Cloud-Infrastruktur gestartet werden können, einschließlich Problemen im Zusammenhang mit der Fastly-Konfiguration, SSL-Zertifikaten, 301-Weiterleitungen und der statischen Asset-Leistung.
exl-id: 3b2c331f-5d90-4051-ada1-4934538fce79
feature: Cache, Cloud, Marketing Tools, Observability, Paas
role: Developer
source-git-commit: d728d44c4e1be3172ebf595122f3cc215207ac17
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 0%

---

# Auf Adobe Commerce in Cloud-Infrastruktur gestartete Blockierungen

Dieser Artikel enthält eine Fehlerbehebung für Blocker, die in Adobe Commerce in der Cloud-Infrastruktur gestartet werden können, einschließlich Problemen im Zusammenhang mit der Fastly-Konfiguration, SSL-Zertifikaten, 301-Weiterleitungen und der statischen Asset-Leistung.

## 1. Schnelle Konfiguration

[Fastly](https://www.fastly.com/) ist ein auf Englisch basierendes Content Delivery Network (CDN) zur Bereitstellung statischer Assets. Sie ist für Adobe Commerce in der Cloud-Infrastruktur in Produktionsumgebungen erforderlich. Daher ist es wichtig, Ihre Website (UAT) schnell zu konfigurieren und zu testen, und zwar sowohl in der Staging- als auch in der Produktionsumgebung.

>[!WARNING]
>
>Wenn der vollständige Seiten-Cache (FPC) aktiviert ist, funktioniert Ihre Website anders. Stellen Sie sicher, dass Sie ihn vor der Live-Schaltung testen.

Der Prozess der Schnellen Konfiguration wird im Abschnitt [Fastly einrichten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) in unserem Benutzerhandbuch ausführlich beschrieben. Im Folgenden finden Sie die wichtigen Schritte.

### (1a) Stellen Sie sicher, dass Sie die neueste Version des Fastly-Moduls installiert haben.

Stellen Sie sicher, dass Sie die neueste Version des Fastly-Moduls installiert haben, um die neuesten Funktionen und Verbesserungen zu erhalten. Um zu überprüfen, ob Sie über die neueste Version von Fastly verfügen, lesen Sie [Upgrade des Fastly-Moduls](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upgrade-the-fastly-module) in unserem Benutzerhandbuch. Weitere Informationen finden Sie unter [Schnelles Einrichten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) in unserem Benutzerhandbuch.

### 1b. Schnelles Aktivieren und Konfigurieren mit dem Commerce Admin

Weitere Informationen finden Sie unter [Schnelle Anmeldeinformationen abrufen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials) in unserem Benutzerhandbuch.

### 1c. Fastly VCL-Snippets hochladen

Weitere Informationen finden Sie unter [Hochladen von VCL auf Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) in unserem Benutzerhandbuch.

Sie können auch [eigene benutzerdefinierte VCL-Snippets erstellen und hinzufügen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html).

### 1d. DNS für Fastly konfigurieren


In diesem Artikel finden Sie detaillierte Schritte: [Schnelles Einrichten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings) in unserem Benutzerhandbuch.

### Verwandte schnelle Artikel in unserer Support-Wissensdatenbank

* [Die schnelle Zwischenspeicherung funktioniert nicht in Cloud](/help/troubleshooting/miscellaneous/fastly-caching-is-not-working-on-magento-cloud.md)
* [Fehler beim Bereinigen des Fastly-Cache in Cloud (Die Bereinigungsanforderung wurde nicht erfolgreich verarbeitet)](/help/troubleshooting/miscellaneous/error-purging-fastly-cache-on-cloud-the-purge-request-was-not-processed-successfully.md)

## 2. Gültiges SSL-Zertifikat (TLS)

Problem: Ohne ein gültiges und funktionierendes SSL-Zertifikat können Sie keine externen Zahlungsmethoden auf der Checkout-Seite in der Staging-Umgebung testen.

Empfehlung **:** Fordern Sie Ihr freigegebenes SSL-Zertifikat für Staging- oder Live-Domänennamen an.


## 3. Konfigurieren und Testen von 301-Weiterleitungen

Problem: 301 Umleitungen werden nicht bereitgestellt oder schlecht konfiguriert, was dazu führt, dass Ihr Store in SEO-Ranglisten und Suchlisten abfällt.

Empfehlung **:** Konfigurieren und testen Sie die 301-Umleitungen sorgfältig.

Wenn Sie von einer alten Website zu einer neuen migrieren, führen die 301-Umleitungen Ihre Kunden von den zuvor indizierten alten Seiten zu den richtigen Seiten in Ihrem neuen Store, wie hier dargestellt:

http://www.mywebsite.com/old-category-page.html **>** http://www.mywebsite.com/new-seo-friendly-category-page.html

**Verwandte Artikel:**

* [Umleitet durch routes.yaml](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/routes/redirects.html) in unserem Benutzerhandbuch.
* [ Leitet über die Cloud-Konsole um](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html) in unserem Benutzerhandbuch.
* [URL schreibt ](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite.html) in unser Benutzerhandbuch um.

## 4. Asset-Leistung

Problem: Statische Assets werden langsam bereitgestellt, sodass Ihre Site eine schlechte Leistung aufweist (lange Ladezeit, nicht angezeigte Multimedia-Inhalte usw.). Statische Assets Ihrer Website sind CSS-Ressourcen, Bilder, Videos, angehängte Dokumente und vieles mehr. Die Art und Weise, wie sie organisiert und bereitgestellt werden, ist ein Schlüsselfaktor für die Leistung Ihrer Site.

Empfehlung: Um mögliche Ursachen für Leistungsmängel zu ermitteln, sollten Sie für Leistungstests das [Adobe Commerce Performance Toolkit](https://github.com/magento/magento2/tree/2.3/setup/performance-toolkit) verwenden. Sie können auch die folgenden Drittanbieter-Tools in Betracht ziehen:

* [Belagerung](https://www.joedog.org/siege-home/): HTTP-Dienstprogramm zum Laden und Benchmarking; unterstützt grundlegende Authentifizierung, Cookies, HTTP, HTTPS und FTP-Protokolle.
* [Jmeter](https://jmeter.apache.org/): Ein seriöses Lasttest- und Leistungsmesswerkzeug. Hilft bei der Messung der Leistung bei erhöhtem Traffic, z. B. bei Flash-Verkäufen.
* [New Relic](https://support.newrelic.com/): Findet Prozesse und Bereiche der Site, die mit der pro Aktion aufgezeichneten Zeit eine langsame Leistung verursachen, z. B. das Senden von Daten, Abfragen, Redis usw.
* [WebPageTest](https://www.webpagetest.org/) (kostenlos) und [Pingdom](https://www.pingdom.com/) (bezahlt): Echtzeitanalyse Ihrer Seiten beim Laden mit verschiedenen Ausgangspunkten.

Sie können auch die [Minimierung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) für CSS, JavaScript und HTML in Betracht ziehen.

**Verwandte Artikel:**

* [Testen Sie die Bereitstellung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production.html) in unserer Entwicklerdokumentation.
