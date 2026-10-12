---
title: 'PWA Studio: Browser kann die Website .local.pwadev nicht auflösen'
description: Dieser Artikel bietet eine Lösung für den Fall, dass ein anderes Programm oder ein anderer Prozess Ihre [Hostdatei] (https://en.wikipedia.org/wiki/Hosts_(file) bearbeitet und den Eintrag für Ihre Projekt-Domain entfernt hat.
exl-id: a1606016-906a-433f-9e40-9faa5f9bd790
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
source-wordcount: '255'
ht-degree: 0%
---
# PWA Studio: Browser kann die Website .local.pwadev nicht auflösen

Dieser Artikel bietet eine Lösung für den Fall, dass ein anderes Programm oder ein anderer Prozess Ihre [Host-Datei]&#x200B;(https://en.wikipedia.org/wiki/Hosts_(file\) bearbeitet und den Eintrag für Ihre Projekt-Domain entfernt hat.

## Betroffene Produkte und Versionen

PWA Studio für Adobe Commerce

## Problem

Beim Navigieren zur Entwicklungs-/Staging-Site wird die `.local.pwadev` Site nicht angezeigt.

## Ursache

Mit PWA Studio können Sie Ihrem lokalen Computer einen benutzerdefinierten Hostnamen und ein SSL-Zertifikat für Ihr Projekt zuweisen. Dazu gehört die Erstellung eines neuen Eintrags in der Hostdatei Ihres Computers, der in etwa wie `my-storefront-project-abc123.local.pwadev` aussieht.

Dieser Eintrag weist jeden Browser auf dem Computer des Entwicklers an, das lokale Storefront-Projekt anzuzeigen, wenn er auf diese URL zugreift. Wenn ein anderes Programm oder ein anderer Prozess diesen Eintrag eingefügt und entfernt hat, weiß der Browser nicht, wohin er gehen soll, und der Browser kann die `.local.pwadev` Site nicht auflösen.

## Lösung

Sie können [Ihre Hostdatei manuell bearbeiten](https://docs.rackspace.com/docs/modify-your-hosts-file), um den Eintrag wieder hinzuzufügen, aber Sie sollten Ihre andere installierte Software überprüfen, um zu sehen, was die vorherige Änderung überschrieben hat.

## Lesen Sie diesbezüglich in unserer Support-Wissensdatenbank

* [PWA Studio: Fehler bei selbstsignierter Zertifikatvertrauensstellung](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio: Webpack bleibt vor Kompilierung hängen](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio: Browser zeigt den Fehler „Proxy nicht möglich für“ an](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio: Validierungsfehler beim Ausführen des Entwicklermodus](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
