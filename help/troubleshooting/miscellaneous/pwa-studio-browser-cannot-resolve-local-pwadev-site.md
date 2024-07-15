---
title: 'PWA Studio: Browser kann die .local.pwadev-Site nicht auflösen.'
description: Dieser Artikel bietet eine Lösung für den Fall, dass ein anderes Programm oder Prozess Ihre [Hostdatei](https://en.wikipedia.org/wiki/Hosts_(file\) bearbeitet und den Eintrag für Ihre Projektdomäne entfernt hat.
exl-id: a1606016-906a-433f-9e40-9faa5f9bd790
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# PWA Studio: Browser kann die .local.pwadev-Site nicht auflösen

Dieser Artikel bietet eine Lösung für den Fall, dass ein anderes Programm oder Prozess Ihre [Host-Datei](https://en.wikipedia.org/wiki/Hosts_(file\) bearbeitet und den Eintrag für Ihre Projekt-Domäne entfernt hat.

## Betroffene Produkte und Versionen

PWA Studio für Adobe Commerce

## Problem

Wenn Sie zur Dev-/Staging-Site navigieren, können Sie die `.local.pwadev`-Site nicht sehen.

## Ursache

Mit PWA Studio können Sie Ihrem lokalen Computer einen benutzerdefinierten Hostnamen und ein SSL-Zertifikat für Ihr Projekt zuweisen. Dazu gehört das Erstellen eines neuen Eintrags in der Hostdatei Ihres Computers, der ungefähr `my-storefront-project-abc123.local.pwadev` aussieht.

Dieser Eintrag weist alle Browser auf dem Computer des Entwicklers an, sich das lokale Storefront-Projekt anzusehen, wenn es auf diese URL zugreift. Wenn ein anderes Programm oder Prozess einging und diesen Eintrag entfernt hat, wusste der Browser nicht, wohin er gehen sollte, und der Browser kann die `.local.pwadev`-Site nicht auflösen.

## Lösung

Sie können Ihre Hostdatei [ manuell bearbeiten, um den Eintrag wieder einzufügen, aber Sie sollten Ihre andere installierte Software überprüfen, um zu sehen, was die vorherige Änderung überschrieben hat.](https://support.rackspace.com/how-to/modify-your-hosts-file/)

## Verwandtes Lesen in unserer Wissensdatenbank

* [PWA Studio: Selbstsignierter Zertifikattrust-Fehler](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio: Webpack hängt vor Beginn der Kompilierung](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio: Browser zeigt den Fehler &quot;Proxy zu kann nicht ausgeführt werden&quot;an](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio: Validierungsfehler beim Ausführen des Entwicklermodus](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
