---
title: Holiday Surge Capacity Requests für Adobe Commerce in unserer Cloud-Infrastruktur
description: Während der Hauptsaison (etwa Mitte November bis Mitte Januar) empfiehlt Adobe allen auf unserer Cloud-Infrastruktur gehosteten Adobe Commerce-Händlern, sich auf den erhöhten Traffic vorzubereiten.
exl-id: 9d6910bf-30bc-4117-bf7f-a0316f9506b5
feature: Cloud, Paas
role: Admin
source-git-commit: 9cd7eeb6af379fa94e234bb677b532051079995c
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# Holiday Surge Capacity Requests für Adobe Commerce in unserer Cloud-Infrastruktur

Während der Hauptsaison (etwa Mitte November bis Mitte Januar) empfiehlt Adobe allen auf unserer Cloud-Infrastruktur gehosteten Adobe Commerce-Händlern, sich auf den erhöhten Traffic vorzubereiten.

Eine umfassende lösungsübergreifende Checkliste und Best Practices für die Vorbereitung Ihrer Systeme und Teams auf die Hauptsaison finden Sie im Handbuch [Adobe DX Unified Holiday Readiness](https://experienceleague.adobe.com/en/docs/support-resources/data-sheets/unified-holiday-readiness).

**Planung und Schätzung des Traffic**

Wir empfehlen allen Adobe Commerce-Händlern in unserer Cloud-[ (verwenden Sie diese Reihe von Empfehlungen zur Schätzung des Traffics in der Spitzensaison](https://business.adobe.com/blog/how-to/the-5-ps-of-peak-season-performance-a-guide-to-preparing-your-infrastructure-for-high-traffic) für die Spitzenumsatzsaison an Feiertagen jedes Jahr.

Nachdem Sie die empfohlene Schätzung abgeschlossen haben und ein Datum gefunden haben, an dem Sie zusätzliche Kapazität benötigen, fahren Sie mit dem nächsten Schritt fort, um Informationen zum Anfordern von Spitzenkapazität zu erhalten.

**Verlauf der Upsides anzeigen**

Sie können den Verlauf der angeforderten Größenänderungen anzeigen, indem Sie die Informationen von Ihrem **CSM (Customer Success Manager) anfordern**.
Für jede Größenänderungsanfrage stehen die folgenden Informationen zur Verfügung:

* **Startdatum der Größe**: Datum der Upsize-Anfrage.
* **Enddatum der Größe**: Datum, an dem der Cluster seine vorherige Größe zurückerhalten hat.
* **vCPU-**: Die Größe des Clusters nach der Vergrößerung.
* **Tage Nutzung**: für wie viele Tage der Cluster im Upsizer verblieben ist.
* **Zeitraum vCPU**: Die vCPU-Größe wurde um die Anzahl der Tage geändert, die sie verwendet wurde. (Beispiel: vCPU-Größe 192 x 25 Tage entspricht 4.800).

**Überspannungskapazität anfordern**

Adobe Commerce-Händler in unserer Cloud-Infrastruktur, die davon ausgehen, dass während der Urlaubszeit zusätzliche Kapazität benötigt wird, sollten [ein Ticket zur Unterstützung der ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize.html) über unser [Hilfezentrum](/help/overview.md) einreichen, in dem die Daten und der erwartete Kapazitätsbedarf innerhalb des Tickets angegeben sind. Bitte beachten Sie, dass eine höhere Kapazität die Nutzung Ihrer lizenzierten Überschusskapazität erfordert.

**Wir empfehlen, diese Tickets mindestens 48 Geschäftsstunden vor dem Zeitpunkt einzureichen, an dem die Kapazität benötigt wird. Darüber hinaus empfehlen wir, Anfragen für die Black Friday / Cyber Monday Periode so weit wie möglich im Voraus zu stellen, da die Kapazität in diesem Zeitraum begrenzt ist.**


**Weitere Hilfe?**

Benötigen Sie weitere Anleitungen zur Vorbereitung auf den Traffic in der Hochsaison? Adobe Commerce-Händler in unserer Cloud-Infrastruktur können sich an ihr Adobe-Account-Team wenden, um Hilfe, Strategie und Planungstipps für die Vorbereitung auf eine erfolgreiche Hochsaison zu erhalten. Wir empfehlen auch, den [Magento Blog](https://magento.com/blog) zu besuchen, um ganzjährig Strategietipps zu erhalten.

## Ressourcen zur Überprüfung Ihrer Kapazität

In unserer Support-Wissensdatenbank:

* [CPU-Zuordnungsberechnung für Adobe Commerce in Cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
* [Überprüfen Sie, ob für Adobe Commerce on Cloud ein Upsize für die Host-Instanzen erforderlich ist](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
* [Überprüfen Sie die CPU-Konfiguration des Hosts für Adobe Commerce in der Cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* [Identifizieren und Messen von Ausfällen für Adobe Commerce in der Cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html)
