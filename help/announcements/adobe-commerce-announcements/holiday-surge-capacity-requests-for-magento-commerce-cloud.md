---
title: Anforderungen an die Ferienkapazität von Adobe Commerce in unserer Cloud-Infrastruktur
description: Während der Sommerferien (ungefähr Mitte November bis Mitte Januar) empfiehlt Adobe, dass sich alle Adobe Commerce-Händler, die in unserer Cloud-Infrastruktur gehostet werden, auf einen erhöhten Traffic vorbereiten.
exl-id: 9d6910bf-30bc-4117-bf7f-a0316f9506b5
feature: Cloud, Paas
role: Admin
source-git-commit: dfd3f788f42677b631ffb5b3153a1c79c2cc1ca3
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Anforderungen an die Ferienkapazität von Adobe Commerce in unserer Cloud-Infrastruktur

Während der Sommerferien (ungefähr Mitte November bis Mitte Januar) empfiehlt Adobe, dass sich alle Adobe Commerce-Händler, die in unserer Cloud-Infrastruktur gehostet werden, auf einen erhöhten Traffic vorbereiten.

**Planung und Schätzung des Traffics**

Es wird empfohlen, dass alle Adobe Commerce-Händler in unserer Cloud-Infrastruktur [Nutzen Sie diese Empfehlungen zur Schätzung des Traffics in der Hochsaison.](https://business.adobe.com/blog/how-to/the-5-ps-of-peak-season-performance-a-guide-to-preparing-your-infrastructure-for-high-traffic) für die Weihnachtszeit jedes Jahr.

Wenn Sie die empfohlene Schätzung abgeschlossen haben und Ihr Team Daten identifiziert hat, von denen Sie glauben, dass Sie zusätzliche Kapazitäten benötigen, fahren Sie mit dem nächsten Schritt fort, um Informationen dazu zu erhalten, wie Sie eine Überspannungskapazität anfordern können.

**Anzeigen des Verlaufs Ihrer Upgrades**

Sie können den Verlauf der angeforderten Größenänderungen in Ihrem [Projekt-Portal (Onboarding-Benutzeroberfläche)](https://devdocs.magento.com/cloud/onboarding/onboarding-tasks.html), unter **Projekt** > **Dienste** > **CPU-Nutzungsverfolgung**.
Die folgenden Informationen stehen für jede Größenanforderung zur Verfügung:

* **Startdatum der Größe**: Datum der Aktualisierungsanfrage.
* **Enddatum der Größe**: Datum, an dem der Cluster auf die vorherige Größe zurückgesetzt wurde.
* **vCPU-Größe**: die Größe des Clusters nach der Upsize-Datei.
* **Nutzung von Tagen**: Wie viele Tage lang wurde der Cluster aktualisiert.
* **Period vCPU**: Die vCPU-Größe wurde um die Anzahl der Tage geändert, für die sie verwendet wurde. (z. B. die vCPU-Größe 192 x 25 Tage entspricht 4.800).

**Anfordern der Überlastungskapazität**

Adobe Commerce-Händler in unserer Cloud-Infrastruktur, die während der Weihnachtssaison zusätzliche Kapazitäten benötigen, sollten [Senden eines Tickets zur Unterstützung der Übernahmekapazität](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize.html) über [Hilfe-Center](/help/overview.md), unter Angabe des Datums und des voraussichtlichen Kapazitätsbedarfs im Fahrschein. Bitte beachten Sie, dass für eine höhere Kapazität die Nutzung Ihrer lizenzierten Überlebenskapazität erforderlich ist.

**Es wird empfohlen, diese Tickets mindestens 48 Geschäftszeiten vor dem Zeitpunkt einzureichen, an dem die Kapazität benötigt wird. Zusätzlich wird empfohlen, die Anfragen für den Black Friday/Cyber Montag-Zeitraum so weit wie möglich im Voraus zu stellen, da die Kapazität während dieses Zeitraums begrenzt ist.**


**Weitere Hilfe?**

Benötigen Sie weitere Anleitungen zur Vorbereitung auf den Traffic in der Hochsaison? Adobe Commerce-Händler in unserer Cloud-Infrastruktur können sich an ihr Adobe-Account-Team wenden, um Hilfe, Strategie und Planungstipps für die Vorbereitung auf eine erfolgreiche Spitzensaison zu erhalten. Wir empfehlen auch, die [Magento Blog](https://magento.com/blog) für Strategietipps ganzjährig.

## Ressourcen zur Überprüfung Ihrer Kapazität

In unserer Support-Wissensdatenbank:

* [Berechnung der CPU-Zuordnung für Adobe Commerce in Cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
* [Überprüfen Sie, ob für Adobe Commerce in Cloud ein Upsize für Host-Instanzen erforderlich ist.](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
* [Überprüfen der CPU-Konfiguration des Hosts für Adobe Commerce in Cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* [Identifizieren und Messen von Ausfällen für Adobe Commerce in Cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html)
