---
title: Kundenprofile werden nicht auf Experience Platform angezeigt
description: Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Ihre Kundenprofildaten bei Verwendung der Erweiterung [!DNL Data Connection] nicht auf der Experience Platform angezeigt werden.
feature: Personalization, Integration, Configuration
role: Admin, Developer
source-git-commit: a520ef45f1c55dbf34a98c4f4d3ab49814535434
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# Kundenprofile werden nicht auf Experience Platform angezeigt

In diesem Artikel finden Sie Schritte zur Fehlerbehebung, wenn Ihre Kundenprofildaten bei Verwendung der Datenverbindungs-Erweiterung nicht auf der Experience Platform angezeigt werden.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.x mit installierter [!DNL Data Connection]-Erweiterung

## Problem

Sie haben die Erweiterung [[!DNL Data Connection]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) installiert und konfiguriert und die Übermittlung von Kundenprofildaten an die Experience Platform aktiviert, aber diese Profildaten werden nicht auf der Experience Platform angezeigt.

## Lösung

Wenn Kundenprofilinformationen nicht auf der Experience Platform angezeigt werden, überprüfen Sie Folgendes:

### Vergewissern Sie sich, dass die neueste Version von [!DNL Data Connection] installiert ist

Stellen Sie sicher, dass Sie die neueste Version der `experience-platform-connector` -Erweiterung installiert haben.

Weitere Informationen zur neuesten Version finden Sie in den Versionshinweisen zur Erweiterung [[!DNL Data Connection]  .](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/release-notes)

>[!NOTE]
>
>Die neueste Version der [!DNL Data Connection] -Erweiterung enthält das `customers-connector` -Modul, das für das Senden von Profildaten an die Experience Platform verantwortlich ist. Das Modul `customers-connector` sollte Version `1.2.0` oder höher sein.

### Bestätigen der Konfiguration des Kunden-Connector-Moduls

Vergewissern Sie sich, dass das `customers-connector`-Modul basierend auf Ihrem Installationsszenario konfiguriert ist.

#### Adobe Commerce on Cloud-Infrastruktur

1. Aktivieren Sie die globale Variable `ENABLE_EVENTING` in `.magento.env.yaml`. [Weitere Infos](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global).

   ```bash
       stage:
           global:
               ENABLE_EVENTING: true
   ```

1. Übernehmen und pushen Sie aktualisierte Dateien in die Cloud-Umgebung. Wenn die Bereitstellung abgeschlossen ist, aktivieren Sie das Senden von Ereignissen mit dem folgenden Befehl:

   ```bash
       bin/magento config:set adobe_io_events/eventing/enabled 1
   ```

#### Vor-Ort-Installation von Adobe Commerce

Führen Sie die folgenden Befehle aus, um die Codegenerierung und Adobe Commerce-Ereignisse zu aktivieren:

```bash
   bin/magento events:generate:module
   bin/magento module:enable Magento_AdobeCommerceEvents
   bin/magento setup:upgrade
   bin/magento setup:di:compile
   bin/magento config:set adobe_io_events/eventing/enabled 1
```

### Bestätigen, dass Sie die Erfassung und Übermittlung von Profildaten an Experience Platform aktiviert haben

Stellen Sie in Commerce Admin sicher, dass die folgenden Felder festgelegt sind:

* Überprüfen Sie in **[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Data Connection]**, ob die Kontrollkästchen [!UICONTROL Back office events] und [!UICONTROL Customer profiles] aktiviert sind.
* Stellen Sie sicher, dass das Feld *[!UICONTROL Profile Dataset ID]* korrekt ist und einen anderen Datensatz enthält als den, den Sie derzeit für Verhaltens- und Back-Office-Ereignisdaten verwenden.

### Überprüfen, ob Ereignisse zu Staging oder Produktion weitergeleitet werden

1. Führen Sie den folgenden Befehl aus, um die aktuelle Adobe Developer-Umgebung anzuzeigen:

   ```bash
   Copy code
   bin/magento config:show
   adobe_io_events/integration/adobe_io_environment
   ```

1. Wenn die Umgebung auf *[!UICONTROL Stage]* festgelegt ist, ändern Sie sie mit dem folgenden Befehl in *[!UICONTROL Production]*:

   ```bash
   Copy code
   bin/magento config:set adobe_io_events/integration/adobe_io_environment
   production
   ```

### Tabelle &quot;Abfrage von Ereignisdaten - SaaS&quot;

Verbinden Sie die folgende SQL-Abfrage und führen Sie sie aus, um zu überprüfen, ob Kundenprofildatensätze im
`event_data_saas` und dass keine Fehler vorliegen:

```sql
Copy code
select * from event_data_saas;
```

### Fehler bei der Ereignisveröffentlichung beheben

1. Wenn der folgende Fehler auftritt, stellen Sie sicher, dass die Sandbox- und Produktions-SaaS-Connector-Schlüssel korrekt sind:

   ```css
   Copy code
   2024-06-07 14:37:57 | 2024-06-07 14:38:03 | 1 | 0 | Event publishing
   failed: Error code: 403; reason: Forbidden { "error": { "code":
   "Forbidden", "message": "Client ID is invalid", "details": {
   "error_code": "403003" } } }
   ```

1. Rufen Sie die Seite &quot;*[!UICONTROL Commerce Services Connector]*&quot;im Admin auf und stellen Sie sicher, dass die angegebenen [!UICONTROL sandbox/production]-Schlüssel korrekt konfiguriert sind. Bestätigen Sie außerdem, dass die Einstellungen für das Commerce-Konto [!UICONTROL sandbox/production] mit denen in der [!UICONTROL Commerce Services Connector] übereinstimmen. Lernen Sie [mehr](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas#apikey).

### Überprüfen Sie, ob sich die Dienst-ID in der Zulassungsliste &quot;&quot;befindet, und bestätigen Sie mit dem Adobe Commerce-Support.

1. Stellen Sie sicher, dass die [!UICONTROL Commerce Services Connector] `serviceId` in der Zulassungsliste in Adobe Commerce angezeigt wird.
1. Wenden Sie sich an den [Adobe Commerce-Support](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) , um den Status der Zulassungsliste zu bestätigen.

## Verwandtes Lesen

Weitere Informationen finden Sie unter der Erweiterung [[!DNL Data Connection]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) im Benutzerhandbuch zu Commerce Services.
