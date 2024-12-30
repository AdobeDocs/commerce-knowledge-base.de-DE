---
title: 'PWA Studio: Validierungsfehler beim Ausführen des Entwicklermodus'
description: In diesem Abschnitt wird eine Lösung für Fälle beschrieben, in denen Validierungsfehler beim Ausführen des Entwicklermodus in Progressive Web App (PWA) Studio für Adobe Commerce auftreten, da zuvor das venia-Konzept (Venia ist eine PWA-Storefront) nicht erstellt wurde. Diese Datei enthält die Variablen für Ihre lokale Entwicklungsumgebung.
exl-id: 97d042ef-88e6-4eda-a834-2cff4de276e2
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# PWA Studio: Validierungsfehler beim Ausführen des Entwicklermodus

In diesem Abschnitt wird eine Lösung für Fälle beschrieben, in denen Validierungsfehler beim Ausführen des Entwicklermodus in Progressive Web App (PWA) Studio für Adobe Commerce auftreten, da zuvor das venia-Konzept (Venia ist eine PWA-Storefront) nicht erstellt wurde. Diese Datei enthält die Variablen für Ihre lokale Entwicklungsumgebung.

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

* Dokumentation zu [PWA Studio für Adobe Commerce](https://magento.github.io/pwa-studio/)
* [Venia-Storefront (Konzept)](https://magento.github.io/pwa-studio/venia-pwa-concept/)
