---
title: Anfordern der Aktualisierung der Cloud-Infrastruktur auf temporäre Adobe Commerce
description: Wenn Ihr Unternehmen ein Online-Ereignis plant, bei dem Sie mit hohem Traffic rechnen, oder Sie plötzlich feststellen, dass Ihre Site ein Ereignis mit hohem Traffic durchläuft, können Sie ein [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) einreichen, um temporäre zusätzliche Cloud-Kapazität für Ihre Adobe Commerce im Cloud-Infrastrukturspeicher anzufordern.
exl-id: 561e2bdd-718a-45c1-8b6c-a0e3a6c8ad04
feature: Cloud, Iaas
source-git-commit: a445bae7f013b29cb83fc96eb26dcbfd186a4de7
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 0%

---

# Anfordern der Aktualisierung der Cloud-Infrastruktur auf temporäre Adobe Commerce

Wenn Ihr Unternehmen ein Online-Ereignis plant, bei dem Sie einen hohen Traffic erwarten, oder Sie plötzlich feststellen, dass Ihre Site ein hohes Traffic-Ereignis durchläuft, können Sie eine [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) , um temporäre zusätzliche Cloud-Kapazität für Ihre Adobe Commerce im Cloud-Infrastrukturspeicher anzufordern.

>[!NOTE]
>
>Für Anfragen ohne Notfall-Upsize ist eine 48-Stunden-Benachrichtigung erforderlich. Aktualisierungen für Werbekampagnen werden nicht als Notfälle betrachtet, es sei denn, die Site ist vollständig funktionsunfähig oder erhält einen viel höheren Traffic als erwartet und die Leistung wurde stark beeinträchtigt.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle [unterstützte Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Ermitteln von Ereignissen mit hohem Traffic

In New Relic-Warnhinweisen können Sie mithilfe von Baseline-Warnbedingungen Schwellenwerte definieren, die sich an das Verhalten Ihrer Daten anpassen.

Grundlegende Warnhinweise eignen sich für die Erstellung von Warnbedingungen, die:

* Melden Sie sich nur dann, wenn sich Daten ungewöhnlich verhalten.
* Dynamische Anpassung an sich ändernde Daten und Trends, einschließlich täglicher oder wöchentlicher Trends.

Darüber hinaus funktioniert die Grundlinienwarnung bei neuen Anwendungen gut, wenn Sie noch kein bekanntes Verhalten haben.

Weitere Informationen zu New Relic finden Sie unter diesem Link [Anomalieerkennung mit angewandter Intelligenz](https://docs.newrelic.com/docs/alerts-applied-intelligence/applied-intelligence/anomaly-detection/anomaly-detection-applied-intelligence/).

Wenn Sie eine Warnmeldung erhalten, die auf ein hohes Traffic-Ereignis hinweist, sollten Sie [Senden eines Support-Tickets](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) Anforderung zusätzlicher Kapazitäten. Führen Sie die folgenden Schritte aus.

## So überwachen Sie die Leistung Ihrer Site

Adobe bietet eine Reihe von New Relic-Warnrichtlinien für Adobe Commerce in der Cloud-Infrastruktur Pro-Planarchitektur und Adobe Commerce in der Starter-Planarchitektur der Cloud-Infrastruktur, um die folgenden wichtigen Leistungsmetriken zu verfolgen:

* [Apdex-Ergebnis](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)
* Fehlerrate
* Speicherplatz (nur in Produktionsumgebungen der Pro-Architektur verfügbar)

Basierend auf Best Practices der Branche legen diese Richtlinien Schwellenwerte für Warn- und kritische Bedingungen fest, die sich auf die Leistung auswirken. Wenn auf Ihrer Site ein Infrastruktur- oder Anwendungsproblem auftritt, bei dem der Trigger eine Alarmschwelle erreicht, sendet New Relic Warnhinweise, damit Sie das Problem proaktiv beheben können. Um diese Richtlinien verwenden zu können, müssen Sie die Benachrichtigungskanäle konfigurieren, damit die Warnhinweise empfangen werden.

Auf diesem Link erfahren Sie, wie Sie [leistungsbasierte Warnhinweise konfigurieren](/docs/commerce-cloud-service/user-guide/monitor/new-relic.html#monitor-performance-with-managed-alerts).

## Schritte zum Anfordern der temporären Größe

Gehen Sie wie folgt vor, um eine [Support-Ticket](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) um temporäre zusätzliche Cloud-Kapazität anzufordern:

Senden einer [Support-Ticket im Adobe Commerce Support Center](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)nach Eingabe der folgenden Informationen:

>[!NOTE]
>
>Die *Urlaubsüberstiegsanforderung* Die Auswahl ist nur eine Option zwischen Oktober und Dezember.

1. Wählen Sie das Adobe Commerce-Produkt aus, für das Sie Support anfordern möchten.
1. Füllen Sie die ersten vier Felder (Produkt, Organisation, Implementierungstyp, Betreff) aus.
1. Auswählen *Adobe Commerce-Cloud-Infrastruktur* im **Kontaktgrund** angezeigt.
1. Auswählen *Anforderung von Holiday-Überkapazitäten* im **Kontaktgrund für Adobe Commerce-Infrastruktur** Dropdown-Optionen. Klicks **OK** in der Pop-up-Nachricht, in der 48 Geschäftszeiten für temporäre Anfragen zur zusätzlichen Cloud-Kapazität angefordert werden.
1. Datumsangaben für die Pflichtfelder auswählen **Größe des Startdatums ändern** und **Enddatum ändern**. Die bevorzugte **Größe der Startzeit ändern** ist auch ein Pflichtfeld.
1. Füllen Sie die nächsten vier Felder aus.
1. Im **Beschreibung** Wenn Sie zusätzliche Informationen zur Größe haben, geben Sie diese hier an. Wenn keine spezifische größere Größe angefordert wird, werden wir Sie auf die nächstgrößere Umgebungsgröße vergrößern. Für Anforderungen vom Typ &quot;Umstieg&quot;wird standardmäßig die nächstgrößere als für die aktuelle Größe verwendet. Wenn Sie zusätzliche Kapazität benötigen, geben Sie bitte dies in der Variablen **Beschreibung** -Feld. Erhöhte Kapazität wird von Ihren vertraglich vereinbarten Surge Days oder vCPU Tagen abgezogen. Das typische Fenster zur Kapazitätssteigerung beträgt fünf Tage. Wenn Sie jedoch mehr oder weniger Tage benötigen, geben Sie dies bitte in Ihrem [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

>[!NOTE]
>
>Sobald die Upsize geplant ist, passt ein automatisiertes System die Größe Ihrer Cloud-Instanz an. Nach Abschluss des Verfahrens erhalten Sie keine Ticketbenachrichtigung. Sie können das Tool &quot;Observation for Adobe Commerce&quot;verwenden, um Ihre AWS- oder Azure-Instanztypen für [die Änderung überprüfen](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md).

## Anzeigen des Verlaufs Ihrer Upgrades

Sie können den Verlauf der angeforderten Größenänderungen in Ihrem [Projekt-Portal (Onboarding-Benutzeroberfläche)](/docs/commerce-cloud-service/start/onboarding.html#cloud-project-portal-(onboarding-ui)), unter **Projekt** > **Dienste** > **CPU-Nutzungsverfolgung**.
Die folgenden Informationen stehen für jede Größenanforderung zur Verfügung:

* **Startdatum der Größe**: Datum der Aktualisierungsanfrage.
* **Enddatum der Größe**: Datum, an dem der Cluster auf die vorherige Größe zurückgesetzt wurde.
* **vCPU-Größe**: die Größe des Clusters nach der Upsize-Datei.
* **Nutzung von Tagen**: Wie viele Tage lang wurde der Cluster aktualisiert.
* **Period vCPU**: Die vCPU-Größe wurde um die Anzahl der Tage geändert, für die sie verwendet wurde. (z. B. die vCPU-Größe 192 x 25 Tage entspricht 4.800).


## Verwandtes Lesen

* Einblicke, Methoden und Beispiele zur Messung und Verbesserung der Site-Leistung finden Sie in den folgenden ausführlichen Artikeln in unserer Support-Wissensdatenbank:
   * [Berechnung der CPU-Zuordnung für Adobe Commerce in Cloud](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
   * [Überprüfen Sie, ob für Adobe Commerce in Cloud eine Upsize für Host-Instanzen erforderlich ist.](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
   * [Überprüfen der CPU-Konfiguration des Hosts für Adobe Commerce in Cloud](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* Informationen zur Erkennung von Ausfällen finden Sie unter [Identifizieren und Messen von Ausfällen für Adobe Commerce in Cloud](/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html) in unserer Wissensdatenbank.
* Informationen zur Verbesserung der Site-Leistung, um zu vermeiden, dass eine Steigerung der Kapazität verwendet werden muss, finden Sie in diesen Artikeln in unserer Entwicklerdokumentation:
   * [Bildgröße](/docs/commerce-admin/catalog/products/digital-assets/product-image-config.html#product-image-resizing)
   * [Zwischenspeicherung von vollständigen Seiten](/docs/commerce-admin/systems/tools/cache-management.html#full-page-caching)
   * [ECE-Tools](/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)
