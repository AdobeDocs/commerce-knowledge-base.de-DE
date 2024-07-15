---
title: Anfordern der Aktualisierung der Cloud-Infrastruktur auf temporäre Adobe Commerce
description: Wenn Ihr Unternehmen ein Online-Ereignis plant, bei dem Sie mit hohem Traffic rechnen, oder Sie plötzlich feststellen, dass Ihre Site ein Ereignis mit hohem Traffic durchläuft, können Sie ein [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) einreichen, um temporäre zusätzliche Cloud-Kapazität für Ihre Adobe Commerce im Cloud-Infrastrukturspeicher anzufordern.
exl-id: 561e2bdd-718a-45c1-8b6c-a0e3a6c8ad04
feature: Cloud, Iaas
source-git-commit: 357e0acb1c849079ff0fe9f53fe386f60475c7f9
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 0%

---

# Anfordern der Aktualisierung der Cloud-Infrastruktur auf temporäre Adobe Commerce

Wenn Ihr Unternehmen ein Online-Ereignis plant, bei dem Sie mit hohem Traffic rechnen, oder Sie plötzlich feststellen, dass Ihre Site ein hohes Traffic-Ereignis durchläuft, können Sie ein [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) einreichen, um temporäre zusätzliche Cloud-Kapazität für Ihre Adobe Commerce im Cloud-Infrastrukturspeicher anzufordern.

>[!NOTE]
>
>Für Anfragen ohne Notfall-Upsize ist eine 48-Stunden-Benachrichtigung erforderlich. Aktualisierungen für Werbekampagnen werden nicht als Notfälle betrachtet, es sei denn, die Site ist vollständig funktionsunfähig oder erhält einen viel höheren Traffic als erwartet und die Leistung wurde stark beeinträchtigt.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle [unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Ermitteln von Ereignissen mit hohem Traffic

In New Relic-Warnhinweisen können Sie mithilfe von Baseline-Warnbedingungen Schwellenwerte definieren, die sich an das Verhalten Ihrer Daten anpassen.

Grundlegende Warnhinweise eignen sich für die Erstellung von Warnbedingungen, die:

* Melden Sie sich nur dann, wenn sich Daten ungewöhnlich verhalten.
* Dynamische Anpassung an sich ändernde Daten und Trends, einschließlich täglicher oder wöchentlicher Trends.

Darüber hinaus funktioniert die Grundlinienwarnung bei neuen Anwendungen gut, wenn Sie noch kein bekanntes Verhalten haben.

Folgen Sie diesem Link, um mehr über die New Relic [Anomalieerkennung mit angewendeter Intelligenz](https://docs.newrelic.com/docs/alerts-applied-intelligence/applied-intelligence/anomaly-detection/anomaly-detection-applied-intelligence/) zu erfahren.

Wenn Sie eine Warnmeldung erhalten, die auf ein hohes Traffic-Ereignis hinweist, sollten Sie in Erwägung ziehen, [ein Support-Ticket zu senden](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket), um zusätzliche Kapazität anzufordern. Führen Sie die folgenden Schritte aus.

## So überwachen Sie die Leistung Ihrer Site

Adobe bietet eine Reihe von New Relic-Warnrichtlinien für Adobe Commerce in der Cloud-Infrastruktur Pro-Planarchitektur und Adobe Commerce in der Starter-Planarchitektur der Cloud-Infrastruktur, um die folgenden wichtigen Leistungsmetriken zu verfolgen:

* [Apdex-Wert](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)
* Fehlerrate
* Speicherplatz (nur in Produktionsumgebungen der Pro-Architektur verfügbar)

Basierend auf Best Practices der Branche legen diese Richtlinien Schwellenwerte für Warn- und kritische Bedingungen fest, die sich auf die Leistung auswirken. Wenn auf Ihrer Site ein Infrastruktur- oder Anwendungsproblem auftritt, bei dem der Trigger eine Alarmschwelle erreicht, sendet New Relic Warnhinweise, damit Sie das Problem proaktiv beheben können. Um diese Richtlinien verwenden zu können, müssen Sie die Benachrichtigungskanäle konfigurieren, damit die Warnhinweise empfangen werden.

Folgen Sie diesem Link, um zu erfahren, wie Sie [leistungsbasierte Warnhinweise konfigurieren](/docs/commerce-cloud-service/user-guide/monitor/new-relic.html#monitor-performance-with-managed-alerts).

## Schritte zum Anfordern der temporären Größe

Gehen Sie wie folgt vor, um ein [Support-Ticket](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) zu senden, um eine temporäre zusätzliche Cloud-Kapazität anzufordern:

Senden Sie ein [Support-Ticket beim Adobe Commerce Support Center](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), nachdem Sie die folgenden Informationen eingegeben haben:

>[!NOTE]
>
>Die Auswahl der *Urlaubsüberziehungsanforderung* ist nur eine Option zwischen Oktober und Dezember.

1. Wählen Sie das Adobe Commerce-Produkt aus, für das Sie Support anfordern möchten.
1. Füllen Sie die ersten vier Felder (Produkt, Organisation, Implementierungstyp, Betreff) aus.
1. Wählen Sie *Adobe Commerce-Cloud-Infrastruktur* in der Dropdown-Liste **Kontaktgrund** aus.
1. Wählen Sie in den Dropdown-Optionen **Adobe Commerce Infrastructure Contact Reason** die Option *Anfrage zur Erhöhung der Urlaubskapazität* aus. Klicken Sie in der Popup-Nachricht auf **OK** , um 48 Geschäftsstunden für temporäre Anfragen mit zusätzlicher Cloud-Kapazität anzufordern.
1. Wählen Sie Datumswerte für die erforderlichen Felder **Größe des Anfangsdatums ändern** und **Größe des Enddatums ändern** aus. Die bevorzugte **Neugröße der Startzeit ändern** ist ebenfalls ein Pflichtfeld.
1. Füllen Sie die nächsten vier Felder aus.
1. Wenn Sie im Feld **Beschreibung** zusätzliche Informationen zur Größe haben, geben Sie sie hier an. Wenn keine spezifische größere Größe angefordert wird, werden wir Sie auf die nächstgrößere Umgebungsgröße vergrößern. Für Anforderungen vom Typ &quot;Umstieg&quot;wird standardmäßig die nächstgrößere als für die aktuelle Größe verwendet. Wenn Sie zusätzliche Kapazität benötigen, geben Sie dies im Feld **Beschreibung** an. Erhöhte Kapazität wird von Ihren vertraglich vereinbarten Surge Days oder vCPU Tagen abgezogen. Das typische Fenster zur Kapazitätssteigerung beträgt fünf Tage. Wenn Sie mehr oder weniger Tage benötigen, geben Sie dies jedoch in Ihrem [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) an.

>[!NOTE]
>
>Sobald die Upsize geplant ist, passt ein automatisiertes System die Größe Ihrer Cloud-Instanz an. Nach Abschluss des Verfahrens erhalten Sie keine Ticketbenachrichtigung. Sie können das Tool &quot;Observation for Adobe Commerce&quot;verwenden, um Ihre AWS- oder Azure-Instanztypen anzuzeigen und [die Änderung zu überprüfen](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md).

## Anzeigen des Verlaufs Ihrer Upgrades

Sie können den Verlauf der angeforderten Größenänderungen anzeigen, indem Sie die Informationen aus Ihrem **CSM (Customer Success Manager)** anfordern.
Die folgenden Informationen stehen für jede Größenanforderung zur Verfügung:

* **Größe des Startdatums**: Datum der Aktualisierungsanforderung.
* **Größe des Enddatums**: Datum, an dem der Cluster zur vorherigen Größe zurückgegeben wurde.
* **vCPU-Größe**: Die Größe des Clusters nach der Upsize.
* **Nutzung der Tage**: Wie viele Tage lang wurde der Cluster aktualisiert.
* **Period vCPU**: Die vCPU-Größe wurde um die Anzahl der Tage geändert, für die sie verwendet wurde. (z. B. die vCPU-Größe 192 x 25 Tage entspricht 4.800).


## Verwandtes Lesen

* Einblicke, Methoden und Beispiele zur Messung und Verbesserung der Site-Leistung finden Sie in den folgenden ausführlichen Artikeln in unserer Support-Wissensdatenbank:
   * [Berechnung der CPU-Zuordnung für Adobe Commerce in Cloud](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
   * [Überprüfen Sie, ob für Adobe Commerce in Cloud ein Upsize für Host-Instanzen erforderlich ist.](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
   * [Überprüfen der CPU-Konfiguration des Hosts für Adobe Commerce in Cloud](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* Informationen zum Identifizieren von Ausfällen finden Sie unter [Identifizieren und Messen von Ausfällen für Adobe Commerce on Cloud](/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html) in unserer Support-Wissensdatenbank.
* Informationen zur Verbesserung der Site-Leistung, um zu vermeiden, dass eine Steigerung der Kapazität verwendet werden muss, finden Sie in diesen Artikeln in unserer Entwicklerdokumentation:
   * [Bildgröße](/docs/commerce-admin/catalog/products/digital-assets/product-image-config.html#product-image-resizing)
   * [Zwischenspeicherung von vollständigen Seiten](/docs/commerce-admin/systems/tools/cache-management.html#full-page-caching)
   * [ECE-Tools](/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)
