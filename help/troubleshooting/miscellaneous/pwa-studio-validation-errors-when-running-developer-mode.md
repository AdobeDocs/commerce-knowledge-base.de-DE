---
title: 'PWA Studio: Validierungsfehler beim Ausführen des Entwicklermodus'
description: In diesem Abschnitt wird eine Lösung für Fälle beschrieben, in denen bei der Ausführung des Entwicklermodus in PWA Studio (Progressive Web App) für Adobe Commerce Validierungsfehler auftreten, da zuvor das Venia-Konzept nicht erstellt wurde (Venia ist eine PWA-Storefront). Umgebungsdatei. Diese Datei enthält die Variablen für Ihre lokale Entwicklungsumgebung.
exl-id: 97d042ef-88e6-4eda-a834-2cff4de276e2
feature: Configuration
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%
---
# PWA Studio: Validierungsfehler beim Ausführen des Entwicklermodus

In diesem Abschnitt wird eine Lösung für Fälle beschrieben, in denen bei der Ausführung des Entwicklermodus in PWA Studio (Progressive Web App) für Adobe Commerce Validierungsfehler auftreten, da zuvor das Venia-Konzept nicht erstellt wurde (Venia ist eine PWA-Storefront). Umgebungsdatei. Diese Datei enthält die Variablen für Ihre lokale Entwicklungsumgebung.

## Betroffene Produkte und Versionen

* PWA Studio für Adobe Commerce

## Problem

<u>Schritt zur Reproduktion</u>:

* Ausführen des Entwicklermodus in PWA Studio für Adobe Commerce.

<u>Erwartetes Ergebnis</u>:

* Der PWA Studio-Server wird normal gestartet.

<u>Tatsächliches </u>:

* Validierungsfehler werden angezeigt, die in etwa wie folgt aussehen können:

```
    ⓧ  Missing required environment variables:         MAGENTO_BACKEND_URL: Connect to an instance of Adobe Commerce 2.3 by specifying its public domain name. (eg.         "https://master-7rqtwti-mfwmkrjfqvbjk.us-4.magentosite.cloud/")      ⚠  No .env file in ./packages/venia-concept. Autogenerate a .env file by running the command 'buildpack         create-env-file ./packages/venia-concept'.
```

## Ursache

Die Umgebungsvariablendatei für die lokale Entwicklungsumgebung fehlt. Die Datei, die der folgende Befehl generiert, enthält die Variablen für Ihre lokale Entwicklungsumgebung.

## Lösung

Stellen Sie sicher, dass Sie den Befehl ausführen

```
npx @magento/pwa-buildpack create-env-file packages/venia-concept
```

im Stammverzeichnis speichern, um die Datei zu generieren, die die Variablen für Ihre lokale Entwicklungsumgebung enthält.

## Verwandtes Lesen

* [Dokumentation zu PWA Studio für Adobe Commerce](https://developer.adobe.com/commerce/pwa-studio/)
* [Venia-Storefront (Konzept)](https://developer.adobe.com/commerce/pwa-studio/guides/packages/venia/)
