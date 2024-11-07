---
title: Fehler während der Bereitstellung beim Upgrade auf eine Version, die PHP 8.1 unterstützt
description: Dieser Artikel bietet eine Lösung für den Fehler, der während der Implementierung auftritt, wenn auf eine Version aktualisiert wird, die PHP 8.1 unterstützt.
exl-id: bdc4a355-4f2b-49a7-9c5d-63c950f7ca30
feature: Deploy, Observability
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Fehler während der Bereitstellung beim Upgrade auf eine Version, die PHP 8.1 unterstützt

Dieser Artikel bietet eine Lösung für den Fehler, der während der Implementierung auftritt, wenn auf eine Version aktualisiert wird, die PHP 8.1 unterstützt.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.4.4 und höher

* Erweiterung oder Technologie (Fastly, New Relic, etc.) Version PHP 8.1

## Problem

Der folgende Fehler tritt während der Implementierung auf, wenn auf eine Version aktualisiert wird, die PHP 8.1 unterstützt.

```PHP
{{E: Error parsing configuration files:

applications: Uncaught exception: The "json" extension is not supported for php:8.1
at <script>:109:12
throw("The \"" + unsupported_extensions[0] + "\" extension is not supported for " + service.type);
^
E: Error: Invalid configuration files, aborting build}}
```

## Ursache

PHP 8.1 beinhaltet bereits JSON-Unterstützung und erfordert nicht, dass die Erweiterung separat installiert wird.

## Lösung

Entfernen Sie JSON aus dem Abschnitt **Laufzeit** > **Erweiterungen** in `.magento.app.yaml` und stellen Sie es erneut bereit.

## Verwandtes Lesen

[PHP-Anwendung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/php-settings) in unserer Entwicklerdokumentation.
