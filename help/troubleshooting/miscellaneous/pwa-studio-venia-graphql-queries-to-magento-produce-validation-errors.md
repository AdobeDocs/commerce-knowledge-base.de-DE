---
title: "PWA Studio: Venia GraphQL-Abfragen an Adobe Commerce führen zu Überprüfungsfehlern."
description: Dieser Artikel enthält Empfehlungen zur Lösung des Problems, bei dem Venia-Storefront-GraphQL-Abfragen an die Adobe Commerce-Instanz Überprüfungsfehler verursachen.
exl-id: ba268945-2a10-4af5-8089-cde21f0687bd
feature: GraphQL
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# PWA Studio: Venia GraphQL-Abfragen an Adobe Commerce führen zu Überprüfungsfehlern

Dieser Artikel enthält Empfehlungen zur Lösung des Problems, bei dem Venia-Storefront-GraphQL-Abfragen an die Adobe Commerce-Instanz Überprüfungsfehler verursachen.

## Betroffene Produkte und Versionen

* Adobe Commerce lokal 2.2.x, 2.3.x
* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x
* PWA Studio-Projekt für Adobe Commerce

## Problem

Venia GraphQL fragt bei lokalen Adobe Commerce- oder Adobe Commerce-Anfragen zur Cloud-Infrastruktur nach Validierungsfehlern.

## Ursache

Einer der Gründe für das Problem könnte die Venia sein, deren GraphQL-Abfragen nicht mit dem Schema der verbundenen Adobe Commerce-Instanz synchronisiert sind.

## Lösung

Um zu testen, ob Ihre Abfragen aktuell sind, führen Sie den folgenden Befehl im Projektstamm aus:

```bash
yarn run validate-queries
```

Dadurch wird ein Kompatibilitätsbericht angezeigt. Wenn Sie Inkompatibilitäten haben, müssen Sie Ihr PWA Studio oder Ihre Adobe Commerce-Instanz aktualisieren. Überprüfen Sie die [Adobe Commerce-Kompatibilitätsmatrix](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/version-compatibility/) um zu sehen, welche Versionen Sie benötigen.

Anweisungen zum Aktualisieren finden Sie in der folgenden Dokumentation:

* Suchen Sie für PWA Studio-Upgrades nach dem Abschnitt &quot;Upgrade von einer früheren Version&quot;des [PWA-Versionshinweise](https://github.com/magento/pwa-studio/releases/) für die Version, auf die Sie aktualisieren müssen.
* [Aktualisierung der Adobe Commerce-Version der Cloud-Infrastruktur](https://devdocs.magento.com/cloud/project/project-upgrade.html) in unserer Entwicklerdokumentation
* [Aktualisieren Sie Adobe Commerce lokal (installiert mit &quot;Composer create-project&quot;oder &quot;archive&quot;)](https://devdocs.magento.com/guides/v2.3/comp-mgr/cli/cli-upgrade.html) in unserer Entwicklerdokumentation
* [Vor Ort Aktualisierung von Adobe Commerce (installiert durch Klonen von Adobe Commerce Repo)](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/dev_update-magento.html) in unserer Entwicklerdokumentation

## Verwandtes Lesen

* [PWA Studio: Webpack hängt vor Beginn der Kompilierung](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md) in unserer Wissensdatenbank
* [PWA Studio: Validierungsfehler beim Ausführen des Entwicklermodus](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md) in unserer Wissensdatenbank
* [PWA Studio: Browser zeigt den Fehler &quot;Proxy zu nicht möglich&quot;an](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md) in unserer Wissensdatenbank
* [Konfigurieren von NPM für die Verwendung von PWA Studio](/help/how-to/general/configure-npm-to-be-able-to-use-pwa-studio.md) in unserer Wissensdatenbank
* [PWA für Adobe Commerce-Dokumentation](https://magento.github.io/pwa-studio/)
