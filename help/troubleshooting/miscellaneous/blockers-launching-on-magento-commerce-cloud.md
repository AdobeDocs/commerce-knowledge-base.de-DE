---
title: Blocker beim Start auf Adobe Commerce in der Cloud-Infrastruktur
description: Dieser Artikel bietet eine Fehlerbehebung für Blocker, die auf Adobe Commerce in der Cloud-Infrastruktur starten, einschließlich Problemen mit der Fastly-Konfiguration, SSL-Zertifikaten, 301-Weiterleitungen und der statischen Asset-Leistung.
exl-id: 3b2c331f-5d90-4051-ada1-4934538fce79
feature: Cache, Cloud, Marketing Tools, Observability, Paas
role: Developer
source-git-commit: d653957b94127e8b1d37a66c069a618f34ac5af9
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---

# Blocker beim Start auf Adobe Commerce in der Cloud-Infrastruktur

Dieser Artikel bietet eine Fehlerbehebung für Blocker, die auf Adobe Commerce in der Cloud-Infrastruktur starten, einschließlich Problemen mit der Fastly-Konfiguration, SSL-Zertifikaten, 301-Weiterleitungen und der statischen Asset-Leistung.

## &#x200B;1. Fastly-Konfiguration

[Fastly](https://www.fastly.com/) ist ein auf Varnish basierendes Content Delivery Network (CDN) zur Bereitstellung statischer Assets. Sie ist für Adobe Commerce in der Cloud-Infrastruktur in Produktionsumgebungen erforderlich. Daher ist es wichtig, Fastly zu konfigurieren und Ihre Website (UAT) mit Fastly zu testen, das sowohl in Staging- als auch in Produktionsumgebungen aktiviert und konfiguriert ist.

>[!WARNING]
>
>Wenn der vollständige Seitencache (FPC) aktiviert ist, funktioniert Ihre Website anders. Stellen Sie sicher, dass Sie sie vor der Live-Schaltung testen.

Der Prozess der Fastly-Konfiguration wird ausführlich im Thema [Einrichten von Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=de) in unserem Benutzerhandbuch dokumentiert. Im Folgenden finden Sie die wichtigsten Schritte.

### 1a. Stellen Sie sicher, dass Sie die neueste Version des Fastly-Moduls installiert haben

Stellen Sie sicher, dass Sie die neueste Version des Fastly-Moduls installiert haben, um die neuesten Funktionen und Verbesserungen zu erhalten. Um zu überprüfen, ob Sie die neueste Version von Fastly haben, lesen Sie [Upgrade des Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=de#upgrade-the-fastly-module) in unserem Benutzerhandbuch. Weitere Informationen finden Sie unter [Fastly einrichten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=de) in unserem Benutzerhandbuch.

### 1b. Schnelles Aktivieren und Konfigurieren mit Commerce Admin

Weitere Informationen finden Sie [Abrufen Ihrer Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=de#get-fastly-credentials) in unserem Benutzerhandbuch.

### 1c. Hochladen von Fastly VCL-Snippets

Weitere Informationen finden Sie unter [VCL in Fastly &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=de).

Sie können auch [eigene benutzerdefinierte VCL-Snippets erstellen und &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html?lang=de).

### 1d. Konfigurieren des DNS für Fastly


Detaillierte Schritte finden Sie in diesem Artikel: [Fastly einrichten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=de#update-dns-configuration-with-development-settings) in unserem Benutzerhandbuch.

## &#x200B;2. Gültiges SSL-Zertifikat (TLS)

Problem: Ohne gültiges und funktionierendes SSL-Zertifikat können Sie keine externen Zahlungsmethoden auf der Checkout-Seite testen - in der Staging-Umgebung.

Empfehlung **:** Sie Ihr freigegebenes SSL-Zertifikat für Staging- oder Live-Domain-Namen an.


## &#x200B;3. Konfigurieren und Testen von 301-Weiterleitungen

Problem: 301-Weiterleitungen werden nicht bereitgestellt oder sind schlecht konfiguriert, was dazu führt, dass Ihr Store in SEO-Rankings und Suchlisten sinkt.

Empfehlung **:** Richten Sie die 301-Weiterleitungen sorgfältig ein und testen Sie sie.

Wenn Sie von einer alten Website zu einer neuen migrieren, leitet der 301 Ihre Kunden von den zuvor indizierten alten Seiten zu den richtigen Seiten in Ihrem neuen Store um, wie hier zu sehen:

http://www.mywebsite.com/old-category-page.html **>** http://www.mywebsite.com/new-seo-friendly-category-page.html

**Verwandte Artikel:**

* [Weiterleitungen über routes.yaml](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/routes/redirects.html?lang=de) in unserem Benutzerhandbuch.
* [Weiterleitungen über die Cloud-Konsole](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=de) in unserem Benutzerhandbuch.
* [URL-Neuschreibungen](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite.html?lang=de) in unserem Benutzerhandbuch.

## &#x200B;4. Asset-Performance

Problem: Statische Assets werden langsam bereitgestellt, sodass Ihre Site eine schlechte Leistung aufweist (lange Ladezeit, nicht angezeigte Multimedia-Inhalte usw.). Statische Assets Ihrer Website sind CSS-Ressourcen, Bilder, Videos, angehängte Dokumente und vieles mehr. Die Art und Weise, wie diese organisiert und bereitgestellt werden, ist ein wichtiger Faktor für die Leistung Ihrer Site.

Empfehlung: Um mögliche Ursachen für schlechte Leistung zu identifizieren, sollten Sie das [Adobe Commerce Performance Toolkit](https://github.com/magento/magento2/tree/2.3/setup/performance-toolkit) für Leistungstests verwenden. Sie können auch die folgenden Drittanbieter-Tools berücksichtigen:

* [Siege](https://www.joedog.org/siege): HTTP-Lasttests und Benchmarking-Dienstprogramm; unterstützt einfache Authentifizierung, Cookies, HTTP-, HTTPS- und FTP-Protokolle.
* [JMeter](https://jmeter.apache.org/): Ein seriöses Tool zur Lastprüfung und Leistungsmessung. Hilft bei der Messung der Leistung bei Traffic-Spitzen, z. B. bei Flash-Verkäufen.
* [New Relic](https://support.newrelic.com/): Findet Prozesse und Bereiche der Site, die eine langsame Leistung mit der verfolgten Zeit pro Aktion verursachen, z. B. bei der Übertragung von Daten, Abfragen, Redis usw.
* [WebPageTest](https://www.webpagetest.org/) (kostenlos) und [Pingdom](https://www.pingdom.com/) (gebührenpflichtig): Echtzeit-Analyse der Ladezeit Ihrer Site-Seiten mit verschiedenen Ursprungsorten.

Sie können auch eine [Minimierung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=de) für CSS, JavaScript und HTML in Betracht ziehen.

**Verwandte Artikel:**

* [Testen der Bereitstellung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production.html?lang=de) in unserer Entwicklerdokumentation.
