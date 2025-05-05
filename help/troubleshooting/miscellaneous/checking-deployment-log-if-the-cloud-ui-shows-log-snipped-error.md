---
title: Überprüfen des Bereitstellungsprotokolls, wenn in der Cloud-Benutzeroberfläche der Fehler „Protokoll abgeschnitten“ auftritt
description: Dieser Artikel bietet eine Lösung für das Problem, dass in der Benutzeroberfläche von Adobe Commerce in der Cloud-Infrastruktur die Fehlermeldung „Protokoll abgeschnitten, da zu lang war“ angezeigt wird, wenn versucht wird, das Bereitstellungsprotokoll in der Benutzeroberfläche von Cloud Project anzuzeigen.
exl-id: 04d28741-72c1-4722-be46-425fe136b9a6
feature: Cloud, Deploy, Logs, Paas
role: Developer
source-git-commit: 846df05668b357b9088bcaf605a75c45ab10f1ae
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Bereitstellungsprotokoll wird überprüft, wenn in der Cloud-Benutzeroberfläche ein Fehler *Protokollausschnitt* auftritt

Dieser Artikel bietet eine Lösung für das Problem, dass in der Benutzeroberfläche von Adobe Commerce in der Cloud-Infrastruktur die Fehlermeldung *Protokoll abgeschnitten, weil es zu lang war* beim Versuch, das Bereitstellungsprotokoll in der Benutzeroberfläche des Cloud-Projekts anzuzeigen, angezeigt wird. (Gilt nicht für die [Adobe Commerce Cloud-Konsole](https://console.adobecommerce.com/).)

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

* [Adobe Commerce in Cloud-Infrastruktur > Erstellen und bereitstellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html?lang=de)
* [Adobe Commerce in Cloud-Infrastruktur > Protokolle anzeigen und verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=de)
