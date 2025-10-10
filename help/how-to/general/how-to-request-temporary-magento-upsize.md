---
title: Anfordern einer temporären Adobe Commerce-Aktualisierung in der Cloud-Infrastruktur
description: Wenn Ihr Unternehmen eine Online-Veranstaltung plant, bei der Sie hohen Traffic erwarten, oder Sie plötzlich feststellen, dass auf Ihrer Website ein hohes Traffic-Ereignis stattfindet, können Sie ein [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) einreichen, um vorübergehend zusätzliche Cloud-Kapazität für Ihren Adobe Commerce im Cloud-Infrastrukturspeicher anzufordern.
exl-id: 561e2bdd-718a-45c1-8b6c-a0e3a6c8ad04
feature: Cloud, Iaas
source-git-commit: e59335b67e1f33e138e34cab93ce593836d14b48
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Anfordern einer temporären Adobe Commerce-Aktualisierung in der Cloud-Infrastruktur

Wenn Ihr Unternehmen eine Online-Veranstaltung plant, bei der Sie hohen Traffic erwarten, oder Sie plötzlich feststellen, dass auf Ihrer Site ein hohes Traffic-Ereignis stattfindet, können Sie ein [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) einreichen, um temporäre zusätzliche Cloud-Kapazität für Ihren Adobe Commerce im Cloud-Infrastrukturspeicher anzufordern.

>[!NOTE]
>
>Für nicht-dringende Upsizing-Anfragen ist eine 48-Stunden-Benachrichtigung erforderlich. Upgrades für Werbekampagnen gelten nicht als Notfälle, es sei denn, die Website ist vollständig nicht funktionsfähig oder erhält viel höheren Traffic als erwartet, und die Leistung wurde stark beeinträchtigt.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle [unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## So identifizieren Sie Ereignisse mit hohem Traffic

In New Relic-Warnhinweisen können Sie allgemeine Warnbedingungen verwenden, um Schwellenwerte zu definieren, die dem Verhalten Ihrer Daten angepasst werden können.

Baseline-Warnhinweise sind nützlich für die Erstellung von Warnhinweisbedingungen, die:

* Nur benachrichtigen, wenn sich Daten ungewöhnlich verhalten.
* Dynamische Anpassung an sich ändernde Daten und Trends, einschließlich täglicher oder wöchentlicher Trends.

Außerdem eignen sich Baseline-Warnungen gut für neue Anwendungen, wenn die Verhaltensweisen noch nicht bekannt sind.

Unter diesem Link erfahren Sie mehr über New Relic [Anomalieerkennung mit Applied Intelligence](https://docs.newrelic.com/docs/alerts-applied-intelligence/applied-intelligence/anomaly-detection/anomaly-detection-applied-intelligence/).

Wenn Sie eine Warnmeldung erhalten, die auf ein Ereignis mit hohem Traffic hinweist, sollten Sie ggf. erwägen, [ein Support-Ticket &#x200B;](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket), um zusätzliche Kapazität anzufordern. Führen Sie die folgenden Schritte aus.

## Überwachen der Leistung Ihrer Site

Adobe bietet eine Reihe von New Relic-Warnhinweisrichtlinien für Adobe Commerce in der Cloud-Infrastruktur Pro Planarchitektur und Adobe Commerce in der Cloud-Infrastruktur Starter Planarchitektur Produktionsumgebungen, um die folgenden wichtigen Leistungsmetriken zu verfolgen:

* [APDEX-Punktzahl](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)
* Fehlerrate
* Speicherplatz (nur in Produktionsumgebungen der Pro-Architektur verfügbar)

Basierend auf den Best Practices der Branche setzen diese Richtlinien Schwellenwerte für Warnungen und kritische Bedingungen, die die Leistung beeinträchtigen. Wenn auf Ihrer Site ein Infrastruktur- oder Anwendungsproblem auftritt, das einen Warnschwellenwert in Trigger setzt, sendet New Relic Warnbenachrichtigungen, damit Sie das Problem proaktiv beheben können. Um diese Richtlinien verwenden zu können, müssen Sie Benachrichtigungskanäle konfigurieren, über die Benachrichtigungen empfangen werden.

Unter diesem Link erfahren Sie, wie [leistungsbasierte Warnhinweise konfigurieren](/docs/commerce-cloud-service/user-guide/monitor/new-relic.html#monitor-performance-with-managed-alerts).

## Schritte zum Anfordern einer temporären Vergrößerung

Um temporäre zusätzliche Cloud-Kapazität anzufordern, reichen Sie ein [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) im Adobe Commerce Support Center mit den folgenden Informationen ein:

>[!NOTE]
>
>Die *Holiday Surge Request*-Option ist nur zwischen Oktober und Dezember möglich.

1. Wählen Sie das [!DNL Adobe Commerce] Produkt aus, für das Sie Unterstützung benötigen:
   * [!DNL Commerce Cloud]
   * [!DNL Commerce on Managed Service]

1. Füllen Sie die folgenden Felder aus:
   * **[!UICONTROL Case Title]**
   * **[!UICONTROL Case Description]** *(Stellen Sie sicher, dass diese das Problem und den Kontext klar beschreiben.)*

1. Wählen *Infrastruktur-Änderungsanforderung* aus dem **[!UICONTROL Issue Reason]** Dropdown-Menü aus.

1. Wählen Sie die **[!UICONTROL Environment]** aus dem Dropdown-Menü aus.

1. Wählen Sie die entsprechende **[!UICONTROL Product Version]** aus dem Dropdown-Menü aus.

1. Wählen Sie *Cloud-Projektgröße (vCPU* aus dem **[!UICONTROL Which Infra Change you would like to do today]** Dropdown-Menü aus.

1. **Wählen Sie die[!UICONTROL Architecture]**:
   * *Standardarchitektur:* Wählen Sie *Nächste verfügbare Größe* aus dem **Wählen Sie die Größe aus** Dropdown-Menü.
   * *Skalierte Architektur:* Wenn diese Option ausgewählt ist, ändert sich der Bildschirm und zeigt zwei zusätzliche Felder an:
      * *Größe für Webknoten*
      * *Größe für Dienstknoten* *(geben Sie die gewünschten Größen für jeden Knoten ein.)*

1. Geben Sie die **[!UICONTROL From Date]** im UTC-Format (Datum und Uhrzeit) ein.

1. Geben Sie die **[!UICONTROL To Date]** im UTC-Format (Datum und Uhrzeit) ein.

1. Geben Sie **[!UICONTROL Project URL]** *an (unter https://accounts.magento.cloud/, normalerweise im Format `https://[REGION].magento.cloud/projects/PROJECT_ID`)*

1. Geben Sie die **[!UICONTROL Project ID]** ein.

1. Geben Sie **[!UICONTROL Affected URL]** *an (muss mit `http://` oder `https://` beginnen)*

1. Wählen Sie **[!UICONTROL Priority]** aus.

1. Wählen Sie **[!UICONTROL Business Impact]** aus.

1. Bestätigen Sie **[!UICONTROL Time Zone]** *(z. B. `(UTC-5:00) Indiana (East)`)*

1. Geben Sie **[!UICONTROL Phone Number]** *ein (z. B. `+12015550123`)*

1. Klicken Sie auf **[!UICONTROL Submit]** , um Ihren Support-Fall abzuschließen.

>[!NOTE]
>
>Sobald die Vergrößerung geplant ist, passt ein automatisiertes System die Größe Ihrer Cloud-Instanz an. Sie erhalten möglicherweise keine Ticket-Benachrichtigung, wenn der Vorgang abgeschlossen ist. Sie können das Tool Observation for Adobe Commerce verwenden, um Ihre AWS- oder Azure-Instanztypen anzuzeigen [die Änderung zu &#x200B;](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md).

## Verlauf der Upsides anzeigen

Sie können den Verlauf der angeforderten Größenänderungen anzeigen, indem Sie die Informationen von Ihrem **CSM (Customer Success Manager) anfordern**.
Für jede Größenänderungsanfrage stehen die folgenden Informationen zur Verfügung:

* **Startdatum der Größe**: Datum der Upsize-Anfrage.
* **Enddatum der Größe**: Datum, an dem der Cluster seine vorherige Größe zurückerhalten hat.
* **vCPU-**: Die Größe des Clusters nach der Vergrößerung.
* **Tage Nutzung**: für wie viele Tage der Cluster im Upsizer verblieben ist.
* **Zeitraum vCPU**: Die vCPU-Größe wurde um die Anzahl der Tage geändert, die sie verwendet wurde. (Beispiel: vCPU-Größe 192 x 25 Tage entspricht 4.800).


## Verwandtes Lesen

* Informationen, Methoden und Beispiele zum Messen und Verbessern der Site-Leistung finden Sie in den folgenden ausführlichen Artikeln in unserer Support-Wissensdatenbank:
   * [CPU-Zuordnungsberechnung für Adobe Commerce in Cloud Service](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
   * [Überprüfen, ob für Adobe Commerce on Cloud ein Upsize für die Instanzen des Hosts erforderlich ist](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
   * [Überprüfen der CPU-Konfiguration des Hosts für Adobe Commerce on Cloud Service](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* Informationen zum Ermitteln von Ausfällen finden Sie unter [Ermitteln und Messen von Ausfällen für Adobe Commerce on Cloud](/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html) in unserer Support-Wissensdatenbank.
* Informationen zur Verbesserung der Site-Leistung, um die Notwendigkeit zu vermeiden, einen Kapazitätszuwachs zu nutzen, finden Sie in diesen Artikeln in unserer Entwicklerdokumentation:
   * [Bildgröße](/docs/commerce-admin/catalog/products/digital-assets/product-image-config.html#product-image-resizing)
   * [Vollständige Seitenzwischenspeicherung](/docs/commerce-admin/systems/tools/cache-management.html#full-page-caching)
   * [ECE-Tools](/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)
