---
title: Fehler während der Bereitstellung beim Upgrade auf eine Version, die PHP 8.1 unterstützt
description: Dieser Artikel bietet eine Lösung für den Fehler, der während der Bereitstellung beim Upgrade auf eine Version auftritt, die PHP 8.1 unterstützt.
exl-id: bdc4a355-4f2b-49a7-9c5d-63c950f7ca30
feature: Deploy, Observability
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%
---
# Fehler während der Bereitstellung beim Upgrade auf eine Version, die PHP 8.1 unterstützt

Dieser Artikel bietet eine Lösung für den Fehler, der während der Bereitstellung beim Upgrade auf eine Version auftritt, die PHP 8.1 unterstützt.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.4.4. und später

* Erweiterung oder Technologie (Fastly, New Relic usw.) Version PHP 8.1

## Problem

Beim Upgrade auf eine Version, die PHP 8.1 unterstützt, tritt während der Bereitstellung der folgende Fehler auf.

```PHP
{{E: Error parsing configuration files:

applications: Uncaught exception: The "json" extension is not supported for php:8.1
at <script>:109:12
throw("The \"" + unsupported_extensions[0] + "\" extension is not supported for " + service.type);
^
E: Error: Invalid configuration files, aborting build}}
```

## Ursache

PHP 8.1 enthält bereits JSON-Unterstützung und erfordert keine separate Installation der Erweiterung.

## Lösung

Entfernen Sie JSON aus dem Abschnitt **Laufzeit** > **Erweiterungen** in `.magento.app.yaml` und stellen Sie es erneut bereit.

## Verwandtes Lesen

[PHP-Anwendung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/php-settings) in unserer Entwicklerdokumentation.
