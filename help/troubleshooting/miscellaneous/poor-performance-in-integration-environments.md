---
title: Schlechte Leistung in Integrationsumgebungen
description: Dieser Artikel bietet eine Lösung für das Problem, dass die Pro-Integrationsumgebungen und die Starter-Staging-Umgebungen schlecht abschneiden.
feature: Integration, Staging
role: Developer
exl-id: 46110dbc-2f54-4654-95e2-39e8ae1e6979
source-git-commit: d7e58d6a9ed8e9b369ea41165cbdd6b362e40824
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Schlechte Leistung in Integrationsumgebungen

Dieser Artikel bietet eine Lösung für das Problem, dass die Pro-Integrationsumgebungen und die Starter-Staging-Umgebungen schlecht abschneiden.

## Betroffene Produkte und Versionen:

* Adobe Commerce auf Cloud-Infrastruktur (alle Versionen)

## Problem

Die Pro-Integrationsumgebung oder die Starter-Staging-Umgebung funktioniert nur schlecht.

## Ursache

Abhängig von der Größe Ihres Katalogs/Ihrer Daten oder den Anforderungen der Integrationen/Anpassungen von Drittanbietern können die in den Integrationsumgebungen verfügbaren Ressourcen überschritten sein.

## Lösung

Um Leistungsprobleme zu beheben, stellen Sie sicher, dass Sie die Best Practices für Best Performance in der Integrationsumgebung befolgen. Möglicherweise müssen Sie auch ein Upgrade der Umgebungen anfordern, um die Integration zu verbessern.

Bestimmen Sie zunächst, ob sich Ihre Umgebung auf der [Erweiterte Integrationskonfiguration](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter) befindet.

* [Pro-Architektur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Starter-Architektur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

Überprüfen Sie das Bereitstellungsprotokoll mit einer der folgenden Methoden.

### Methode 1:

Führen Sie den folgenden Befehl mithilfe der Cloud-CLI aus:

`magento-cloud activity:log -e <branch name>`

### Methode 2:

Überprüfen Sie das neueste Bereitstellungsprotokoll für diese Umgebung in der [Cloud-Konsole](https://console.adobecommerce.com).

Wenn Sie am Ende des Bereitstellungsprotokolls so etwas sehen - die erste Zeile zeigt die Größe=XL, und die übrigen Zeilen zeigen die Größe=L -, bedeutet dies, dass Sie sich in der Konfiguration der erweiterten Integration befinden.

```
Environment configuration
mymagento (type: php:8.2, size: XL, disk: 5120)
mysql (type: mysql:10.6, size: L, disk: 5120)
redis (type: redis:7.2, size: L)
opensearch (type: opensearch:2, size: L, disk: 1024)
rabbitmq (type: rabbitmq:3.12, size: L, disk: 1024)
```

Wenn Sie die Konfiguration der erweiterten Integration nicht verwenden, können Sie [die Verbesserung/das Upgrade anfordern](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter).
Wenn Sie die Konfiguration der erweiterten Integration bereits verwenden oder nach dem Upgrade weiterhin Leistungsprobleme auftreten, sollten Sie die Best Practices für eine optimale Leistung in der Integrationsumgebung befolgen:

* [Pro-Architektur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Starter-Architektur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

Wenn Sie die oben genannten Empfehlungen erfüllt haben, [ Sie (eine Support-Anfrage](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) um zusätzliche Hilfe.
