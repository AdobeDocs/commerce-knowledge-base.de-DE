---
title: Zwischengespeicherte Bilder werden nach der Aktualisierung von 2.2.X auf 2.3.X nicht geladen
description: Dieser Artikel bietet die Lösung für das Problem, dass zwischengespeicherte Bilder nach einem Upgrade von Adobe Commerce auf Cloud-Infrastruktur 2.2.X auf 2.3.X nicht angezeigt werden.
exl-id: 3e6bd5aa-bd5d-4880-8b78-64f280647abe
feature: Cache, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Zwischengespeicherte Bilder werden nach der Aktualisierung von 2.2.X auf 2.3.X nicht geladen

Dieser Artikel bietet die Lösung für das Problem, dass zwischengespeicherte Bilder nach einem Upgrade von Adobe Commerce auf Cloud-Infrastruktur 2.2.X auf 2.3.X nicht angezeigt werden.

## Betroffene Versionen und Editionen:

* Adobe Commerce auf Cloud-Infrastruktur Pro-Planarchitektur 2.2.X, 2.3.X

## Problem

Nachdem Adobe Commerce von 2.2.X auf 2.3.X aktualisiert wurde, sind die zwischengespeicherten Produktbilder nicht verfügbar und stattdessen wird eine 404-Seite angezeigt.

Das Problem wird durch die falsche Nginx-Konfiguration verursacht, die in `.magento.app.yaml`: `index.php` (oder keine) für die `"/media"` statt `passthru: /get.php`.

## Lösung

1. Überprüfen Sie Ihre `.magento.app.yaml` Konfigurationsdatei im `"/media"` Standort. Die richtige Konfiguration sieht wie folgt aus:

   ```yaml
   "/media":
       root: "pub/media"
       allow: true
       scripts: false
       expires: 1y
       passthru: "/get.php"
   ```

1. Wenn `passthru` nicht auf `"/get.php"` und `expires` nicht festgelegt ist, führen Sie die folgenden Schritte aus.
1. Korrigieren Sie die Konfigurationsdatei.
   * Starter Plan: Korrigieren Sie die Datei selbst und übertragen Sie die Änderungen.
   * Pro Plan:
   * Integration: Korrigieren Sie die Datei selbst und übertragen Sie die Änderungen per Push.
   * Staging und Produktion: Korrigieren Sie die Datei selbst, pushen Sie die Änderungen und erstellen Sie eine [Support-Ticket für Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) , damit sie angewendet wird.

1. Schnelle Bildoptimierung in Commerce Admin aktivieren (Fastly muss zuvor konfiguriert werden), wie hier beschrieben: <https://devdocs.magento.com/guides/v2.3/cloud/cdn/fastly-image-optimization.html>.

Wenn die Konfiguration korrekt ist, Sie aber dennoch mit dem Problem konfrontiert sind, setzen Sie die Untersuchung fort oder kontaktieren Sie [Adobe Commerce-Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
