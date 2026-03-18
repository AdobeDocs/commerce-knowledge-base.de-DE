---
title: 'PWA Studio: Webpack bleibt vor Kompilierung hängen'
description: In diesem Artikel wird eine vorgeschlagene Lösung für den Fall vorgestellt, dass ein JavaScript [Webpack](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/#webpack) lange Zeit hängen bleibt, bevor mit der Kompilierung in Progressive Web App Studio (PWA Studio) begonnen wird.
exl-id: 692eeafa-9289-4d66-9f2f-1e0fe36e681d
feature: Configuration
role: Developer
source-git-commit: 032fe4d32921c63570672b9c68e8c03e00bd1077
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# PWA Studio: Webpack bleibt vor Kompilierung hängen

In diesem Artikel wird über eine vorgeschlagene Lösung gesprochen, um zu erkennen, wenn ein JavaScript [Webpack](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/#webpack) lange Zeit hängen bleibt, bevor die Kompilierung in Progressive Web App Studio (PWA Studio) beginnt.

## Betroffene Produkte und Versionen

* PWA Studio

## Problem

[Überprüfen Sie, was die neueste Version des pwa-buildpack ist](https://github.com/magento/pwa-studio/tree/master/packages/pwa-buildpack) und die

```yaml
pwa-buildpack
```

Die Versionsnummer befindet sich neben der `package.json` Dateinamenliste. Wenn Sie über eine alte Version von verfügen

```yaml
pwa-buildpack
```

-Projekt, kann das webpack lange hängen, bevor mit der Kompilierung begonnen wird.

<u>Schritte zur Reproduktion</u>:

<u>Voraussetzungen</u>: Richten Sie eine PWA Studio-Storefront wie Venia mit einer lokalen Adobe Commerce-Instanz ein und führen Sie eine

```yaml
build
```

oder

```yaml
watch
```

Befehl.

<u>Erwartetes Ergebnis</u>:

* Bei Verwendung von    ```yaml    build    ```    generiert die Build-Artefakte für Venia normalerweise.
* Bei Verwendung von    ```yaml    watch    ```    -Befehl, startet sie die Venia-Storefront normal.

<u>Tatsächliches </u>:

Ihr

```yaml
build
```

oder

```yaml
watch
```

Der Befehl scheint angehalten zu sein und wird nicht abgeschlossen, und es werden keine Fehler angezeigt.

## Lösungen

Aktualisieren Sie Ihr Projekt mit dem folgenden Befehl:

```yaml
yarn upgrade
```

Stellen Sie mit dem folgenden Befehl sicher, dass Sie eine aktuelle Version von OpenSSL auf Ihrem System haben:

```yaml
openssl version
```

Die Version sollte 1.0 oder höher sein (oder LibreSSL 2, im Fall von OSX High Sierra.).

Sie können höhere Versionen von OpenSSL mit [Homebrew](https://brew.sh/) unter OSX, [Chocolatey](https://chocolatey.org/) unter Windows oder dem Package Manager Ihrer Linux-Distribution installieren.

## Verwandtes Lesen

* [JavaScript Webpack: Konzepte](https://webpack.js.org/concepts/)
* [Venia-Storefront-Setup](https://developer.adobe.com/commerce/pwa-studio/guides/packages/venia/)
* [PWA Buildpack](https://developer.adobe.com/commerce/pwa-studio/guides/packages/buildpack/)
* [Buildpack-Befehlszeilenschnittstelle](https://developer.adobe.com/commerce/pwa-studio/api/buildpack/cli/)
* [Tools und Bibliotheken: buildpack](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/#webpack)
