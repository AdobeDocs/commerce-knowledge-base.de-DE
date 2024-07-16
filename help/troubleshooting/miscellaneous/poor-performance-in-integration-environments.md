---
title: Schlechte Leistung in Integrationsumgebungen
description: Dieser Artikel bietet eine Lösung für das Problem, dass die Pro-Integrationsumgebungen und Starter-Staging-Umgebungen nur schlecht funktionieren.
feature: Integration, Staging
role: Developer
source-git-commit: c0e2a8fdd2e4d231e56a3121544dbd8a25a8d60c
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Schlechte Leistung in Integrationsumgebungen

Dieser Artikel bietet eine Lösung für das Problem, dass die Pro-Integrationsumgebungen und Starter-Staging-Umgebungen nur schlecht funktionieren.

## Betroffene Produkte und Versionen:

* Adobe Commerce in der Cloud-Infrastruktur (alle Versionen)

## Problem

Ihre Pro-Integration-Umgebung oder Starter-Staging-Umgebung weist eine schlechte Leistung auf.

## Ursache

Je nach der Größe Ihres Katalogs/Ihrer Daten oder den Anforderungen Ihrer Drittanbieterintegrationen/-anpassungen haben die in den Integrationsumgebungen verfügbaren Ressourcen möglicherweise überschritten.

## Lösung

Um Leistungsprobleme zu beheben, stellen Sie sicher, dass Sie die Best Practices für die beste Leistung in der Integrationsumgebung befolgen. Möglicherweise müssen Sie auch ein Upgrade der Umgebungen anfordern, um die Integration zu verbessern.

Bestimmen Sie zunächst, ob Ihre Umgebung sich in der [Konfiguration der erweiterten Integration](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter) befindet.

* [Pro Architecture](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Starterarchitektur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

Überprüfen Sie das Bereitstellungsprotokoll mit einer dieser Methoden.

### Methode 1:

Führen Sie den folgenden Befehl mit der Cloud-CLI aus:

`magento-cloud activity:log -e <branch name>`

### Methode 2:

Überprüfen Sie das neueste Bereitstellungsprotokoll für diese Umgebung in der [Cloud-Konsole](https://console.adobecommerce.com).

Wenn am Ende des Bereitstellungsprotokolls etwas wie dieses angezeigt wird - die erste Zeile zeigt size=XL und die verbleibenden Zeilen zeigen size=L - dann bedeutet das, dass Sie sich in der Konfiguration der erweiterten Integration befinden.

```
Environment configuration
mymagento (type: php:8.2, size: XL, disk: 5120)
mysql (type: mysql:10.6, size: L, disk: 5120)
redis (type: redis:7.2, size: L)
opensearch (type: opensearch:2, size: L, disk: 1024)
rabbitmq (type: rabbitmq:3.12, size: L, disk: 1024)
```

Wenn Sie nicht über die Konfiguration der erweiterten Integration verfügen, können Sie [die Verbesserung/Aktualisierung anfordern](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter).
Wenn Sie bereits mit der Konfiguration der erweiterten Integration arbeiten oder nach der Aktualisierung weiterhin Leistungsprobleme auftreten, sollten Sie die Best Practices für eine optimale Leistung in der Integrationsumgebung befolgen:

* [Pro Architecture](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Starterarchitektur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

Wenn Sie die oben genannten Empfehlungen erfüllt haben, senden Sie [eine Supportanfrage](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket), um zusätzliche Unterstützung zu erhalten.
 
