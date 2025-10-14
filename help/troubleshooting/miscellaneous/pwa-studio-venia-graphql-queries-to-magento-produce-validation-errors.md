---
title: 'PWA Studio: Venia GraphQL-Abfragen an Adobe Commerce erzeugen Validierungsfehler'
description: Dieser Artikel enthält Empfehlungen zur Lösung des Problems, dass Venia-Storefront-GraphQL-Abfragen an die Adobe Commerce-Instanz zu Validierungsfehlern führen.
exl-id: ba268945-2a10-4af5-8089-cde21f0687bd
feature: GraphQL
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# PWA Studio: Venia GraphQL-Abfragen an Adobe Commerce erzeugen Validierungsfehler

Dieser Artikel enthält Empfehlungen zur Lösung des Problems, dass Venia-Storefront-GraphQL-Abfragen an die Adobe Commerce-Instanz zu Validierungsfehlern führen.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.2.x, 2.3.x
* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x
* PWA Studio-Projekt für Adobe Commerce

## Problem

Venia GraphQL-Abfragen an lokale Adobe Commerce-Standorte oder Adobe Commerce in der Cloud-Infrastruktur führen zu Validierungsfehlern.

## Ursache

Einer der Gründe für das Problem kann Venia sein, dessen GraphQL-Abfragen nicht mit dem Schema der verbundenen Adobe Commerce-Instanz synchronisiert sind.

## Lösung

Um zu testen, ob Ihre Abfragen aktuell sind, führen Sie den folgenden Befehl im Projektstamm aus:

```bash
yarn run validate-queries
```

Daraufhin wird ein Kompatibilitätsbericht angezeigt. Wenn Sie Inkompatibilitäten haben, müssen Sie Ihr PWA Studio oder Ihre Adobe Commerce-Instanz aktualisieren. Überprüfen Sie die [Adobe Commerce-Kompatibilitätsmatrix](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/version-compatibility/) um zu sehen, welche Versionen Sie genau benötigen.

In der folgenden Dokumentation finden Sie Anweisungen zum Upgrade:

* Suchen Sie bei PWA Studio-Upgrades in den [PWA-Versionshinweisen nach dem Abschnitt „Upgrade von einer früheren Version](https://github.com/magento/pwa-studio/releases/) für die Version, auf die Sie ein Upgrade durchführen müssen.
* [Upgrade von Adobe Commerce auf die Cloud](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)Infrastrukturversion in unserer Entwicklerdokumentation
* [Upgrade von Adobe Commerce On-Premise (installiert mit „Composer create-project“ oder Archiv)](https://experienceleague.adobe.com/de/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) in unserer Entwicklerdokumentation
* [Upgrade von Adobe Commerce On-Premise (durch Klonen des Adobe Commerce-Repositorys installiert](https://experienceleague.adobe.com/de/docs/commerce-operations/upgrade-guide/developer/git-installs) in unserer Entwicklerdokumentation

## Verwandtes Lesen

* [PWA Studio: Webpack hängt vor der Kompilierung &#x200B;](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md) unserer Support-Wissensdatenbank
* [PWA Studio: Validierungsfehler beim Ausführen des &#x200B;](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md) in unserer Support-Wissensdatenbank
* [PWA Studio: In unserer Support-Wissensdatenbank wird im Browser &#x200B;](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md) Fehler „Proxy nicht möglich“ angezeigt
* [Konfigurieren Sie NPM, um PWA Studio verwenden zu können](/help/how-to/general/configure-npm-to-be-able-to-use-pwa-studio.md) in unserer Support-Wissensdatenbank
* Dokumentation zu [PWA für Adobe Commerce](https://magento.github.io/pwa-studio/)
