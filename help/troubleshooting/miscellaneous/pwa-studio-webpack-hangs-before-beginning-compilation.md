---
title: "PWA Studio: Webpack hängt vor Beginn der Kompilierung"
description: In diesem Artikel wird von einer empfohlenen Lösung gesprochen, wenn ein JavaScript [Webpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack) lange Zeit hängt, bevor mit der Kompilierung in Progressive Web App Studio (PWA Studio) begonnen wird.
exl-id: 692eeafa-9289-4d66-9f2f-1e0fe36e681d
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# PWA Studio: Webpack hängt vor Beginn der Kompilierung

In diesem Artikel wird von einer empfohlenen Lösung gesprochen, wenn ein JavaScript [Webpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack) lange Zeit hängt, bevor mit der Kompilierung in Progressiv Web App Studio (PWA Studio) begonnen wird.

## Betroffene Produkte und Versionen

* PWA Studio

## Problem

[Überprüfen Sie, was die neueste Version des pwa-buildpack ist](https://github.com/magento/pwa-studio/tree/master/packages/pwa-buildpack), und die

```yaml
pwa-buildpack
```

Die Versionsnummer befindet sich neben der Liste mit dem Dateinamen &quot;`package.json`&quot;. Wenn Sie eine alte Version des

```yaml
pwa-buildpack
```

-Projekt, kann das Webpack lange Zeit hängen, bevor mit der Kompilierung begonnen wird.

<u>Zu reproduzierende Schritte</u>:

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

* Wenn Sie die    ```yaml    build    ```    -Befehl, generiert es normalerweise die Build-Artefakte für Venia.
* Wenn Sie die    ```yaml    watch    ```    -Befehl, wird die Venia-Storefront normal gestartet.

<u>Tatsächliches Ergebnis</u>:

Ihre

```yaml
build
```

oder

```yaml
watch
```

-Befehl erscheint angehalten und wird nicht abgeschlossen, und es werden auch keine Fehler angezeigt.

## Lösungen

Aktualisieren Sie Ihr Projekt mit dem folgenden Befehl:

```yaml
yarn upgrade
```

Stellen Sie mithilfe des folgenden Befehls sicher, dass Sie eine aktuelle Version von openssl auf Ihrem System haben:

```yaml
openssl version
```

Die Version sollte 1.0 oder höher sein (oder LibreSSL 2, im Falle von OSX High Sierra.).

Sie können höhere Versionen von OpenSSL mit [Homebrew](https://brew.sh/) unter OSX, [Chocolatey](https://chocolatey.org/) unter Windows oder dem Paketmanager Ihrer Linux-Distribution installieren.

## Verwandtes Lesen

* [Javascript-Webpack: Konzepte](https://webpack.js.org/concepts/)
* [Venia-Storefront-Setup](https://magento.github.io/pwa-studio/venia-pwa-concept/setup/)
* [PWA Buildpack](https://magento.github.io/pwa-studio/pwa-buildpack/)
* [buildpack-Befehlszeilenschnittstelle](https://magento.github.io/pwa-studio/pwa-buildpack/reference/buildpack-cli/)
* [Tools und Bibliotheken: buildpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack)
