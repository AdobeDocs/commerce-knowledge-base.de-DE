---
title: 'PWA Studio: Validierungsfehler beim Ausführen des Entwicklermodus'
description: Dieses Thema behandelt eine Lösung für den Fall, dass Validierungsfehler auftreten, wenn der Entwicklermodus im Progressiven Web App (PWA) Studio für Adobe Commerce ausgeführt wird, da das Venia-Konzept noch nicht erstellt wurde (Venia ist eine PWA-Storefront). -Umgebungsdatei. Diese Datei enthält die Variablen für Ihre lokale Entwicklungsumgebung.
exl-id: 97d042ef-88e6-4eda-a834-2cff4de276e2
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# PWA Studio: Validierungsfehler beim Ausführen des Entwicklermodus

Dieses Thema behandelt eine Lösung für den Fall, dass Validierungsfehler auftreten, wenn der Entwicklermodus im Progressiven Web App (PWA) Studio für Adobe Commerce ausgeführt wird, da das Venia-Konzept noch nicht erstellt wurde (Venia ist eine PWA-Storefront). -Umgebungsdatei. Diese Datei enthält die Variablen für Ihre lokale Entwicklungsumgebung.

## Betroffene Produkte und Versionen

* PWA Studio für Adobe Commerce

## Problem

<u>Zu reproduzierende Schritte</u>:

* Führen Sie den Entwicklermodus in PWA Studio für Adobe Commerce aus.

<u>Erwartetes Ergebnis</u>:

* Der PWA Studio-Server wird normal gestartet.

<u>Tatsächliches Ergebnis</u>:

* Überprüfungsfehler werden angezeigt, die in etwa wie folgt aussehen können:

```
    ⓧ  Missing required environment variables:         MAGENTO_BACKEND_URL: Connect to an instance of Adobe Commerce 2.3 by specifying its public domain name. (eg.         "https://master-7rqtwti-mfwmkrjfqvbjk.us-4.magentosite.cloud/")      ⚠  No .env file in ./packages/venia-concept. Autogenerate a .env file by running the command 'buildpack         create-env-file ./packages/venia-concept'.
```

## Ursache

Die Umgebungsvariablen-Datei für Ihre lokale Entwicklungsumgebung fehlt. Die Datei, die der folgende Befehl generiert, enthält die Variablen für Ihre lokale Entwicklungsumgebung.

## Lösung

Vergewissern Sie sich, dass Sie den Befehl

```
npx @magento/pwa-buildpack create-env-file packages/venia-concept
```

im Stammverzeichnis, um die Datei zu generieren, die die Variablen für Ihre lokale Entwicklungsumgebung enthält.

## Verwandtes Lesen

* [PWA Studio für die Adobe Commerce-Dokumentation](https://magento.github.io/pwa-studio/)
* [Venia-Storefront (Konzept)](https://magento.github.io/pwa-studio/venia-pwa-concept/)
