---
title: Überprüfen des Bereitstellungsprotokolls, wenn die Cloud-Benutzeroberfläche den Fehler "Log Snipped" aufweist
description: Dieser Artikel bietet eine Lösung für das Problem, bei dem die Adobe Commerce auf der Benutzeroberfläche der Cloud-Infrastruktur die Fehlermeldung *log-Snipped anzeigt, da sie zu lang war*, wenn versucht wurde, das Bereitstellungsprotokoll auf der Benutzeroberfläche des Cloud-Projekts anzuzeigen.
exl-id: 04d28741-72c1-4722-be46-425fe136b9a6
feature: Cloud, Deploy, Logs, Paas
role: Developer
source-git-commit: 71bec5b99063d771982f6dcab111b9e5a4aaec69
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Überprüfen des Bereitstellungsprotokolls, ob die Cloud-Benutzeroberfläche *Protokollausschnitt* error

Dieser Artikel bietet eine Lösung für das Problem, bei dem Adobe Commerce in der Benutzeroberfläche der Cloud-Infrastruktur die *Protokollausschnitt, da es zu lang war* Fehlermeldung beim Versuch, das Bereitstellungsprotokoll auf der Benutzeroberfläche des Cloud-Projekts anzuzeigen. (Gilt nicht für die [Adobe Commerce Cloud-Konsole](https://console.adobecommerce.com/).

## Betroffene Produkte

Adobe Commerce in der Cloud-Infrastruktur (alle unterstützten Versionen)

## Problem

Beim Versuch, das Bereitstellungsprotokoll auf der Benutzeroberfläche des Cloud-Projekts anzuzeigen, zeigt Adobe Commerce auf der Benutzeroberfläche der Cloud-Infrastruktur die folgende Fehlermeldung an: *Protokollausschnitt, da es zu lang war*.

## Zu reproduzierende Schritte

1. Navigieren Sie zur Projekt-URL und klicken Sie auf die Schaltfläche **Status** des betreffenden Einsatzes.
1. Wenn das Protokoll zu lang ist, um in der Benutzeroberfläche angezeigt zu werden, wird die Fehlermeldung angezeigt: *Protokollausschnitt, da es zu lang war*.

## Ursache

Beachten Sie, dass das in der Benutzeroberfläche angezeigte Protokoll nicht als &quot;Source of Truth&quot;behandelt werden sollte, insbesondere wenn Sie feststellen, dass die Site nach der Auflistung der Bereitstellung mit dem Status &quot;Success&quot;nicht reagiert oder ordnungsgemäß funktioniert. Sie sollten dies auch mit den Protokollen auf dem Server überprüfen. Siehe Abschnitt [Protokolle anzeigen und verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) in unserer Entwicklerdokumentation.

## Lösung

1. Stellen Sie sicher, dass Sie [Magento Cloud-CLI](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html) in Ihrer lokalen Umgebung installiert.
1. Führen Sie den folgenden Befehl aus:

   ```bash
   magento-cloud activity -p <project id> -e <environment>
   ```

1. Es wird eine Ausgabe zurückgegeben, die der folgenden ähnelt:

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

   Beispiel zur Überprüfung des Protokolls der fehlgeschlagenen Bereitstellung:

   ```bash
   magento-cloud activity:log raah5xrhqz3wg -p <project id> -e <environment>
   ```

## Weitere Informationen finden Sie in unserer Entwicklerdokumentation:

* [Adobe Commerce auf Cloud-Infrastruktur > Erstellen und Bereitstellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html)
* [Adobe Commerce auf Cloud-Infrastruktur > Protokolle anzeigen und verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)
