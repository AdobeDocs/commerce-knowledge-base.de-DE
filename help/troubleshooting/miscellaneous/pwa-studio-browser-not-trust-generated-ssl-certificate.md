---
title: 'PWA Studio: Browser vertraut nicht auf generiertes SSL-Zertifikat'
description: Dieser Artikel bietet eine Lösung für eine nicht vertrauenswürdige, generierte SSL-Zertifikatwarnung in Ihrem Browser, wenn Sie während der Entwicklung zu einer lokalen Instanz Ihrer PWA Studio-Storefront navigieren.
exl-id: b7bfe1e6-5832-4472-9e51-f04b8583428a
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
source-wordcount: '303'
ht-degree: 0%
---
# PWA Studio: Browser vertraut nicht auf generiertes SSL-Zertifikat

Dieser Artikel bietet eine Lösung für eine nicht vertrauenswürdige, generierte SSL-Zertifikatwarnung in Ihrem Browser, wenn Sie während der Entwicklung zu einer lokalen Instanz Ihrer PWA Studio-Storefront navigieren.

## Betroffene Produkte und Versionen

PWA Studio für Adobe Commerce

## Problem

Der Browser vertraut dem generierten SSL-Zertifikat Ihrer lokalen PWA Studio-Storefront nicht.

## Ursache

Navigieren Sie zur Entwicklungs-/Staging-Site.

## Lösung

Führen Sie in Ihrem Storefront-Projekt den Befehl zum Hinzufügen eines benutzerdefinierten Host-Namens und eines SSL-Zertifikats zu Ihrer lokalen Entwicklungsinstanz aus:

```sh
yarn buildpack create-custom-origin ./
```

Das Generieren von Zertifikaten wird von [devcert](https://github.com/davewasmer/devcert) gehandhabt. Es hängt von OpenSSL ab. Stellen Sie daher sicher, dass Sie eine aktuelle Version von openssl auf Ihrem System haben, indem Sie den folgenden Befehl verwenden:

`openssl version`

Die Version sollte 1.0 oder höher sein (oder LibreSSL 2, im Fall von OSX High Sierra).

Sie können höhere Versionen von OpenSSL mit [Homebrew](https://brew.sh/) unter OSX, [Chocolatey](https://chocolatey.org/) unter Windows oder dem Package Manager Ihrer Linux-Distribution installieren.

Wenn Sie Linux verwenden, stellen Sie sicher, dass `libnss3-tools` (oder das Äquivalent) auf Ihrem System installiert ist. Weitere Informationen finden Sie in diesem Abschnitt der [devcert](https://github.com/davewasmer/devcert#skipcertutil) Readme.

Einige Benutzer haben vorgeschlagen, den Ordner „devcert“ zu löschen, um die Zertifikatsregenerierung für den Trigger wiederherzustellen.

* Für MacOS-Benutzer befindet sich dieser Ordner normalerweise unter: `{{~/Library/Application Support/devcert }}`
* Für Windows-Benutzer befindet sich dieser Ordner normalerweise unter: `${User}\AppData\Local\devcert`

## Lesen Sie diesbezüglich in unserer Support-Wissensdatenbank

* [PWA Studio: Fehler bei selbstsignierter Zertifikatvertrauensstellung](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio: Webpack bleibt vor Kompilierung hängen](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio: Der Browser zeigt den Fehler „Proxy nicht möglich für“ an](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio: Validierungsfehler beim Ausführen des Entwicklermodus](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
