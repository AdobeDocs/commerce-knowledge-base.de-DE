---
title: Neue Umgebungen werden in die Produktion verschoben, wenn sie von Git gepusht werden
description: Dieser Artikel bietet eine Lösung für das Problem, dass neue Umgebungen unter der Produktionsumgebung in Adobe Commerce auf der Cloud-Infrastruktur platziert werden, wenn sie vom Git-Versionskontrollsystem gepusht werden.
exl-id: 279cd6d8-fd45-45ba-8456-8b397a01976f
feature: Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%
---
# Neue Umgebungen werden in die Produktion verschoben, wenn sie von Git gepusht werden

Dieser Artikel bietet eine Lösung für das Problem, dass neue Umgebungen unter der Produktionsumgebung in Adobe Commerce auf der Cloud-Infrastruktur platziert werden, wenn sie vom Git-Versionskontrollsystem gepusht werden.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problem

<u>Voraussetzungen</u>:

Verwenden Sie einen lokalen, von Git gesteuerten Klon des Projekts.

<u>Schritte zur Reproduktion</u>:

Sie müssen eine Integrationsverzweigung aus der Staging-Verzweigung erstellen:

1. Wechseln Sie zur Staging-Verzweigung, indem Sie den folgenden Befehl in der lokalen Shell ausführen: `git checkout staging`
1. Erstellen Sie eine Integrationsverzweigung aus der Staging-Verzweigung, indem Sie den folgenden Befehl in der lokalen Shell ausführen: `git checkout -b <branch>`
1. Pushen Sie die Verzweigung in das Remote-Repository und richten Sie eine Upstream-Verzweigung ein, indem Sie den folgenden Befehl in der lokalen Shell ausführen: `git push --set-upstream origin <branch>`

<u>Erwartete Ergebnisse</u>:

Die neue Verzweigung wird unter der Staging-Verzweigung erstellt.

<u>Tatsächliche Ergebnisse</u>:

Die neue Verzweigung wurde unter der Produktionsverzweigung erstellt.

## Ursache

Das ist kein Bug. Zum Einrichten einer übergeordneten Verzweigung für eine andere Verzweigung sollte der Händler die Magento-Cloud-CLI verwenden.

## Lösung

Eine übergeordnete Verzweigung kann erst festgelegt werden, nachdem der Händler eine neu erstellte Verzweigung gepusht und aktiviert hat. Siehe [Adobe Commerce in der Cloud-Infrastruktur > Bitbucket-](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/dev-tools/integrations/bitbucket#create-a-cloud-branch) in unserer Entwicklerdokumentation.

Um eine übergeordnete Seite für die vorhandene Verzweigung auf dem Server zu aktualisieren, verwenden Sie den Befehl `magento-cloud environment:info` in der Magento-Cloud-CLI.

Anwendungsbeispiel:

`magento-cloud environment:info parent Staging`

Dadurch wird die übergeordnete Verzweigung für die aktuell ausgecheckte Verzweigung auf „Staging“ gesetzt.

## Verwandtes Lesen

* [Adobe Commerce auf Cloud-Infrastruktur > magento-cloud CLI](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-overview) in unserer Entwicklerdokumentation.
