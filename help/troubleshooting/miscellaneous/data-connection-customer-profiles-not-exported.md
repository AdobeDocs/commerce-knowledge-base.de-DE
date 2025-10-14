---
title: Kundenprofile werden nicht in Experience Platform angezeigt
description: Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Ihre Kundenprofildaten bei Verwendung der Erweiterung  [!DNL Data Connection]  nicht auf der Experience Platform angezeigt werden.
feature: Personalization, Integration, Configuration
role: Admin, Developer
exl-id: 4f12b032-0bee-47da-927a-8d4c2d8b8276
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# Kundenprofile werden nicht in Experience Platform angezeigt

Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Ihre Kundenprofildaten bei Verwendung der Datenverbindungserweiterung nicht auf der Experience Platform angezeigt werden.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.x mit installierter [!DNL Data Connection]

## Problem

Sie haben die [[!DNL Data Connection]](https://experienceleague.adobe.com/de/docs/commerce-merchant-services/data-connection/overview)-Erweiterung installiert und konfiguriert und das Senden von Kundenprofildaten an die Experience Platform aktiviert, diese Profildaten werden jedoch nicht auf der Experience Platform angezeigt.

## Lösung

Wenn die Kundenprofilinformationen nicht auf der Experience Platform angezeigt werden, überprüfen Sie Folgendes:

### Überprüfen Sie, ob die neueste Version von [!DNL Data Connection] installiert ist

Vergewissern Sie sich, dass Sie die neueste Version der `experience-platform-connector`-Erweiterung installiert haben.

In den [[!DNL Data Connection] Versionshinweisen zur Erweiterung](https://experienceleague.adobe.com/de/docs/commerce-merchant-services/data-connection/release-notes) finden Sie Informationen zur neuesten Version.

>[!NOTE]
>
>Die neueste Version der [!DNL Data Connection]-Erweiterung enthält das `customers-connector`-Modul, das für das Senden von Profildaten an die Experience Platform verantwortlich ist. Das `customers-connector` sollte Version `1.2.0` oder höher sein.

### Überprüfen, ob das Modul „customers-connector“ konfiguriert ist

Bestätigen Sie, dass das `customers-connector` entsprechend Ihrem Installationsszenario konfiguriert ist.

#### Adobe Commerce auf Cloud-Infrastruktur

1. Aktivieren Sie die globale Variable `ENABLE_EVENTING` in `.magento.env.yaml`. [Weitere Informationen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global).

   ```bash
       stage:
           global:
               ENABLE_EVENTING: true
   ```

1. Übertragen und Übertragen aktualisierter Dateien in die Cloud-Umgebung. Wenn die Bereitstellung abgeschlossen ist, aktivieren Sie das Senden von Ereignissen mit dem folgenden Befehl:

   ```bash
       bin/magento config:set adobe_io_events/eventing/enabled 1
   ```

#### Adobe Commerce On-Premise-Installation

Führen Sie die folgenden Befehle aus, um die Codegenerierung und Adobe Commerce-Ereignisse zu aktivieren:

```bash
   bin/magento events:generate:module
   bin/magento module:enable Magento_AdobeCommerceEvents
   bin/magento setup:upgrade
   bin/magento setup:di:compile
   bin/magento config:set adobe_io_events/eventing/enabled 1
```

### Bestätigen Sie, dass die Profildaten erfasst und an Experience Platform gesendet werden konnten.

Stellen Sie in Commerce Admin sicher, dass die folgenden Felder festgelegt sind:

* Stellen Sie in **[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Data Connection]** sicher, dass die Kontrollkästchen [!UICONTROL Back office events] und [!UICONTROL Customer profiles] aktiviert sind.
* Stellen Sie sicher, dass das *[!UICONTROL Profile Dataset ID]* korrekt ist und es sich um einen anderen Datensatz handelt als den, den Sie derzeit für Verhaltens- und Backoffice-Ereignisdaten verwenden.

### Überprüfen, ob Ereignisse zur Staging- oder Produktionsumgebung weitergeleitet werden

1. Führen Sie den folgenden Befehl aus, um die aktuelle Adobe Developer-Umgebung anzuzeigen:

   ```bash
   Copy code
   bin/magento config:show
   adobe_io_events/integration/adobe_io_environment
   ```

1. Wenn die Umgebung auf *[!UICONTROL Stage]* eingestellt ist, ändern Sie sie mithilfe des folgenden Befehls in *[!UICONTROL Production]*:

   ```bash
   Copy code
   bin/magento config:set adobe_io_events/integration/adobe_io_environment
   production
   ```

### SaaS-Tabelle für Abfrageereignisdaten

Stellen Sie eine Verbindung her und führen Sie die folgende [!DNL SQL] aus, um zu überprüfen, ob Kundenprofildatensätze in der
Tabelle `event_data_saas` und dass keine Fehler auftreten:

```sql
Copy code
select * from event_data_saas;
```

### Verarbeiten von Fehlern bei der Ereignisveröffentlichung

1. Wenn der folgende Fehler auftritt, stellen Sie sicher, dass die Sandbox- und Produktions-SaaS-Connector-Schlüssel korrekt sind:

   ```css
   Copy code
   2024-06-07 14:37:57 | 2024-06-07 14:38:03 | 1 | 0 | Event publishing
   failed: Error code: 403; reason: Forbidden { "error": { "code":
   "Forbidden", "message": "Client ID is invalid", "details": {
   "error_code": "403003" } } }
   ```

1. Navigieren Sie zur Seite *[!UICONTROL Commerce Services Connector]* in der Admin Console und stellen Sie sicher, dass die angegebenen [!UICONTROL sandbox/production] korrekt konfiguriert sind. Bestätigen Sie außerdem, dass die Einstellungen der Commerce-[!UICONTROL sandbox/production] mit den in der [!UICONTROL Commerce Services Connector] angezeigten übereinstimmen. Weitere [&#x200B; (](https://experienceleague.adobe.com/de/docs/commerce-merchant-services/user-guides/integration-services/saas#apikey).

### Überprüfen Sie, ob sich die Service-ID in der Zulassungsliste befindet, und bestätigen Sie dies mit dem Adobe Commerce-Support

1. Auf die Zulassungsliste setzen Stellen Sie sicher, dass die [!UICONTROL Commerce Services Connector] `serviceId` in der Adobe Commerces angezeigt wird.
1. Wenden Sie sich an den [Adobe Commerce](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)Support, um den Status der Zulassungsliste zu bestätigen.

## Verwandtes Lesen

* [[!DNL Data Connection]](https://experienceleague.adobe.com/de/docs/commerce-merchant-services/data-connection/overview) im Commerce Services-Benutzerhandbuch
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
