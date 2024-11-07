---
title: Neue Umgebungen, die beim Verschieben aus Git in die Produktionsumgebung eingefügt werden
description: Dieser Artikel bietet eine Lösung für das Problem, dass neue Umgebungen in der Produktionsumgebung von Adobe Commerce in der Cloud-Infrastruktur platziert werden, wenn sie vom Git-Versionskontrollsystem übertragen werden.
exl-id: 279cd6d8-fd45-45ba-8456-8b397a01976f
feature: Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Neue Umgebungen, die beim Verschieben aus Git in die Produktionsumgebung eingefügt werden

Dieser Artikel bietet eine Lösung für das Problem, dass neue Umgebungen in der Produktionsumgebung von Adobe Commerce in der Cloud-Infrastruktur platziert werden, wenn sie vom Git-Versionskontrollsystem übertragen werden.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problem

<u>Voraussetzungen</u>:

Lassen Sie einen lokalen Git-gesteuerten Klon des Projekts haben.

<u>Zu reproduzierende Schritte</u>:

Sie müssen eine Integrationsverzweigung aus der Staging-Verzweigung erstellen:

1. Wechseln Sie zur Staging-Verzweigung, indem Sie den folgenden Befehl in der lokalen Shell ausführen: `git checkout staging`
1. Erstellen Sie eine Integrationsverzweigung aus der Staging-Verzweigung, indem Sie den folgenden Befehl in der lokalen Shell ausführen: `git checkout -b <branch>`
1. Pushen Sie die Verzweigung in das Remote-Repository und richten Sie eine Upstream-Verzweigung ein, indem Sie den folgenden Befehl in der lokalen Shell ausführen: `git push --set-upstream origin <branch>`

<u>Erwartete Ergebnisse</u>:

Die neue Verzweigung wird unter der Staging-Verzweigung erstellt.

<u>Tatsächliche Ergebnisse</u>:

Die neue Verzweigung wurde im Produktionszweig erstellt.

## Ursache

Das ist kein Fehler. Um eine übergeordnete Verzweigung für eine andere Verzweigung festzulegen, sollte der Händler die Befehlszeilenschnittstelle magento-cloud verwenden.

## Lösung

Eine übergeordnete Verzweigung kann erst festgelegt werden, nachdem der Händler eine neu erstellte Verzweigung gepusht und aktiviert hat. Weitere Informationen finden Sie unter [Adobe Commerce unter Cloud-Infrastruktur > Bitbucket-Integration](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/integrations/bitbucket#create-a-cloud-branch) in unserer Entwicklerdokumentation.

Um ein übergeordnetes Element für die vorhandene Verzweigung auf dem Server zu aktualisieren, verwenden Sie den Befehl `magento-cloud environment:info` in der magento-cloud-CLI.

Anwendungsbeispiel:

`magento-cloud environment:info parent Staging`

Dadurch wird die übergeordnete Verzweigung für die derzeit ausgecheckte Verzweigung auf &quot;Staging&quot;gesetzt.

## Verwandtes Lesen

* [Adobe Commerce über Cloud-Infrastruktur > magento-cloud-CLI](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-overview) in unserer Entwicklerdokumentation.
