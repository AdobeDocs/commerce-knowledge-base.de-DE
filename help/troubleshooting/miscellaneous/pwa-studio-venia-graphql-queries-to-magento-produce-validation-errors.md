---
title: "PWA Studio: Venia GraphQL-Abfragen an Adobe Commerce führen zu Überprüfungsfehlern."
description: Dieser Artikel enthält Empfehlungen zur Lösung des Problems, bei dem Venia-Storefront-GraphQL-Abfragen an die Adobe Commerce-Instanz Überprüfungsfehler verursachen.
exl-id: ba268945-2a10-4af5-8089-cde21f0687bd
feature: GraphQL
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Dadurch wird ein Kompatibilitätsbericht angezeigt. Wenn Sie Inkompatibilitäten haben, müssen Sie Ihr PWA Studio oder Ihre Adobe Commerce-Instanz aktualisieren. Überprüfen Sie die [Adobe Commerce-Kompatibilitätsmatrix](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/version-compatibility/) , um zu sehen, welche Versionen genau Sie benötigen.

Anweisungen zum Aktualisieren finden Sie in der folgenden Dokumentation:

* Suchen Sie für PWA Studio-Upgrades im Abschnitt &quot;Upgrade von einer früheren Version&quot;der [PWA-Versionshinweise](https://github.com/magento/pwa-studio/releases/) nach der Version, auf die Sie ein Upgrade durchführen müssen.
* [Aktualisieren Sie Adobe Commerce auf die Cloud-Infrastrukturversion](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) in unserer Entwicklerdokumentation
* [Aktualisieren Sie Adobe Commerce lokal (installiert mit &quot;Composer create-project&quot;oder &quot;archive&quot;)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) in unserer Entwicklerdokumentation
* [Aktualisieren Sie Adobe Commerce lokal (installiert durch Klonen von Adobe Commerce Repo)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/developer/git-installs) in unserer Entwicklerdokumentation

## Verwandtes Lesen

* [PWA Studio: Der Webpack hängt vor Beginn der Kompilierung](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md) in unserer Support-Wissensdatenbank
* [PWA Studio: Validierungsfehler beim Ausführen des Entwicklermodus](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md) in unserer Support-Wissensdatenbank
* [PWA Studio: Browser zeigt in unserer Support-Wissensdatenbank &quot;Kann nicht auf&quot;Fehler](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md) an
* [Konfigurieren Sie NPM so, dass es PWA Studio](/help/how-to/general/configure-npm-to-be-able-to-use-pwa-studio.md) in unserer Support-Wissensdatenbank verwenden kann.
* [PWA für Adobe Commerce-Dokumentation](https://magento.github.io/pwa-studio/)
