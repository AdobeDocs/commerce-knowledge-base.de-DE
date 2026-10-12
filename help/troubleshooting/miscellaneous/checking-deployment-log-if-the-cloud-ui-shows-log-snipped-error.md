---
title: Überprüfen des Bereitstellungsprotokolls, wenn in der Cloud-Benutzeroberfläche der Fehler „Protokoll abgeschnitten“ auftritt
description: Dieser Artikel bietet eine Lösung für das Problem, dass in der Benutzeroberfläche von Adobe Commerce in der Cloud-Infrastruktur die Fehlermeldung „Protokoll abgeschnitten, da zu lang war“ angezeigt wird, wenn versucht wird, das Bereitstellungsprotokoll in der Benutzeroberfläche von Cloud Project anzuzeigen.
exl-id: 04d28741-72c1-4722-be46-425fe136b9a6
feature: Cloud, Deploy, Logs, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: 3c398179-d35a-51ba-b317-6c5b95feef5e
    internal-label: Logs
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%
---
# Bereitstellungsprotokoll wird überprüft, wenn in der Cloud-Benutzeroberfläche ein Fehler *Protokollausschnitt* auftritt

Dieser Artikel bietet eine Lösung für das Problem, dass in der Benutzeroberfläche von Adobe Commerce in der Cloud-Infrastruktur die Fehlermeldung *Protokoll abgeschnitten, weil es zu lang war* beim Versuch, das Bereitstellungsprotokoll in der Benutzeroberfläche des Cloud-Projekts anzuzeigen, angezeigt wird. (Gilt nicht für die [Adobe Commerce Cloud Console](https://console.adobecommerce.com/).)

## Betroffene Produkte

Adobe Commerce auf Cloud-Infrastruktur (alle unterstützten Versionen)

## Problem

Beim Versuch, das Bereitstellungsprotokoll in der Benutzeroberfläche des Cloud-Projekts anzuzeigen, zeigt Adobe Commerce in der Benutzeroberfläche der Cloud-Infrastruktur die folgende Fehlermeldung an: *Protokoll abgeschnitten, weil es zu lang war*.

## Schritte zur Reproduktion

1. Wechseln Sie zur Projekt-URL und klicken Sie auf **Status** der betreffenden Bereitstellung.
1. Wenn das Protokoll zu lang ist, um in der Benutzeroberfläche angezeigt zu werden, wird die folgende Fehlermeldung angezeigt: *Protokoll abgeschnitten, weil es zu lang war*.

## Ursache

Beachten Sie, dass das in der Benutzeroberfläche angezeigte Protokoll nicht als Datenquelle behandelt werden sollte, insbesondere wenn Sie feststellen, dass die Site nicht reagiert oder nicht richtig funktioniert, nachdem die Bereitstellung mit dem Status Erfolgreich aufgeführt wurde. Sie sollten auch mit den Protokollen auf dem Server überprüfen. Siehe [Anzeigen und Verwalten von Protokollen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=de) in unserer Entwicklerdokumentation.

## Lösung

1. Stellen Sie sicher, dass [Magento Cloud CLI](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html?lang=de) in Ihrer lokalen Umgebung installiert ist.
1. Sie können einen der folgenden Befehle ausführen:

   ```bash
   magento-cloud act -p <project id> -e <environment>
   ```

   ```bash
   magento-cloud activity:list -p <project id> -e <environment>
   ```

1. Sie geben eine Ausgabe ähnlich der folgenden zurück:

   ```bash
   Activities on the project <project name> (project id), environment <environment>:
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | ID            | Created                   | Description                         | Progress | State    | Result  |
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | l5wgwmzwrsskg | 2021-06-01T08:18:02-07:00 | ABC merged Integration into Staging | 100%     | complete | success |
   | raah5xrhqz3wg | 2021-06-01T08:07:18-07:00 | XYZ pushed to Integration           | 100%     | complete | failure |
   ```

1. Kopieren Sie die Aktivitäts-ID der betroffenen Bereitstellung und führen Sie dann den Befehl aus:

   ```bash
   magento-cloud activity:log <activity ID> -p <project id> -e <environment>
   ```

   Beispiel zur Untersuchung des Protokolls der fehlgeschlagenen Bereitstellung:

   ```bash
   magento-cloud activity:log raah5xrhqz3wg -p <project id> -e <environment>
   ```

## Weitere Informationen finden Sie in unserer Entwicklerdokumentation:

* [Adobe Commerce auf Cloud-Infrastruktur > Erstellen und Bereitstellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html?lang=de)
* [Adobe Commerce auf Cloud-Infrastruktur > Protokolle anzeigen und verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=de)
