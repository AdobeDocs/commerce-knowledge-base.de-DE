---
title: Anforderungen an die Ferienkapazität von Adobe Commerce in unserer Cloud-Infrastruktur
description: Während der Sommerferien (ungefähr Mitte November bis Mitte Januar) empfiehlt Adobe, dass sich alle Adobe Commerce-Händler, die in unserer Cloud-Infrastruktur gehostet werden, auf einen erhöhten Traffic vorbereiten.
exl-id: 9d6910bf-30bc-4117-bf7f-a0316f9506b5
feature: Cloud, Paas
role: Admin
source-git-commit: 357e0acb1c849079ff0fe9f53fe386f60475c7f9
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# Anforderungen an die Ferienkapazität von Adobe Commerce in unserer Cloud-Infrastruktur

Während der Sommerferien (ungefähr Mitte November bis Mitte Januar) empfiehlt Adobe, dass sich alle Adobe Commerce-Händler, die in unserer Cloud-Infrastruktur gehostet werden, auf einen erhöhten Traffic vorbereiten.

**Planung und Schätzung des Traffics**

Wir empfehlen allen Adobe Commerce-Händlern in unserer Cloud-Infrastruktur [diese Empfehlungen zur Schätzung des Traffics in der Hochsaison ](https://business.adobe.com/blog/how-to/the-5-ps-of-peak-season-performance-a-guide-to-preparing-your-infrastructure-for-high-traffic) für die Weihnachtszeit-Sommerverkaufssaison jedes Jahr zu nutzen.

Wenn Sie die empfohlene Schätzung abgeschlossen haben und Ihr Team Daten identifiziert hat, von denen Sie glauben, dass Sie zusätzliche Kapazitäten benötigen, fahren Sie mit dem nächsten Schritt fort, um Informationen dazu zu erhalten, wie Sie eine Überspannungskapazität anfordern können.

**Anzeigen des Verlaufs Ihrer Upgrades**

Sie können den Verlauf der angeforderten Größenänderungen anzeigen, indem Sie die Informationen aus Ihrem **CSM (Customer Success Manager)** anfordern.
Die folgenden Informationen stehen für jede Größenanforderung zur Verfügung:

* **Größe des Startdatums**: Datum der Aktualisierungsanforderung.
* **Größe des Enddatums**: Datum, an dem der Cluster zur vorherigen Größe zurückgegeben wurde.
* **vCPU-Größe**: Die Größe des Clusters nach der Upsize.
* **Nutzung der Tage**: Wie viele Tage lang wurde der Cluster aktualisiert.
* **Period vCPU**: Die vCPU-Größe wurde um die Anzahl der Tage geändert, für die sie verwendet wurde. (z. B. die vCPU-Größe 192 x 25 Tage entspricht 4.800).

**Anfordern der Überlagerungskapazität**

Adobe Commerce-Händler in unserer Cloud-Infrastruktur, die während der Weihnachtssaison zusätzliche Kapazitäten benötigen, sollten [über unser [Help Center](/help/overview.md) ein Support-Ticket für die Übernahmekapazität einreichen, in dem die Daten und der voraussichtliche Kapazitätsbedarf im Ticket angegeben sind. ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize.html) Bitte beachten Sie, dass für eine höhere Kapazität die Nutzung Ihrer lizenzierten Überlebenskapazität erforderlich ist.

**Wir empfehlen, diese Tickets mindestens 48 Geschäftszeiten vor dem Zeitpunkt einzureichen, zu dem die Kapazität benötigt wird. Außerdem empfehlen wir, die Anfragen für den Black Friday/Cyber Montag so weit wie möglich im Voraus zu stellen, da die Kapazität während dieses Zeitraums begrenzt ist.**


**Weitere Hilfe?**

Benötigen Sie weitere Anleitungen zur Vorbereitung auf den Traffic in der Hochsaison? Adobe Commerce-Händler in unserer Cloud-Infrastruktur können sich an ihr Adobe-Account-Team wenden, um Hilfe, Strategie und Planungstipps für die Vorbereitung auf eine erfolgreiche Spitzensaison zu erhalten. Wir empfehlen auch, das [Magento Blog](https://magento.com/blog) für Strategietipps ganzjährig auszuchecken.

## Ressourcen zur Überprüfung Ihrer Kapazität

In unserer Support-Wissensdatenbank:

* [CPU-Zuordnungsberechnung für Adobe Commerce auf Cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
* [Überprüfen Sie, ob für Adobe Commerce in Cloud ein Upsize für die Hostinstanzen erforderlich ist](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
* [Überprüfen Sie die CPU-Konfiguration des Hosts für Adobe Commerce in der Cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* [Identifizieren und Messen von Ausfällen für Adobe Commerce in Cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html)
