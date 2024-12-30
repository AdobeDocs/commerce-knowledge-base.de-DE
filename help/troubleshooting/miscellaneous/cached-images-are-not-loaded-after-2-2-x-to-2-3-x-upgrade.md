---
title: Zwischengespeicherte Bilder werden nach dem Upgrade von 2.2.x auf 2.3.x nicht geladen
description: Dieser Artikel bietet die Lösung für das Problem, dass zwischengespeicherte Bilder nach dem Upgrade von Adobe Commerce auf Cloud-Infrastruktur 2.2.x auf 2.3.x nicht angezeigt werden.
exl-id: 3e6bd5aa-bd5d-4880-8b78-64f280647abe
feature: Cache, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Zwischengespeicherte Bilder werden nach dem Upgrade von 2.2.x auf 2.3.x nicht geladen

Dieser Artikel bietet die Lösung für das Problem, dass zwischengespeicherte Bilder nach dem Upgrade von Adobe Commerce auf Cloud-Infrastruktur 2.2.x auf 2.3.x nicht angezeigt werden.

## Betroffene Versionen und Ausgaben:

* Adobe Commerce auf Cloud-Infrastruktur Pro planarchitektur 2.2.x, 2.3.x

## Problem

Nach der Aktualisierung von Adobe Commerce von 2.2.x auf 2.3.x sind die zwischengespeicherten Produktbilder nicht mehr verfügbar und stattdessen wird eine 404-Seite angezeigt.

Das Problem wird durch die falsche Nginx-Konfiguration verursacht, die in `.magento.app.yaml` festgelegt ist: `index.php` (oder keine) wird für den `"/media"` Speicherort anstelle von `passthru: /get.php` verwendet.

## Lösung

1. Überprüfen Sie Ihre `.magento.app.yaml`-Konfigurationsdatei am `"/media"` Speicherort. Die korrekte Konfiguration sieht wie folgt aus:

   ```yaml
   "/media":
       root: "pub/media"
       allow: true
       scripts: false
       expires: 1y
       passthru: "/get.php"
   ```

1. Wenn `passthru` nicht auf `"/get.php"` und `expires` nicht eingestellt ist, führen Sie die folgenden Schritte aus.
1. Korrigieren Sie die Konfigurationsdatei.
   * Starterplan: Korrigieren Sie die Datei selbst und übertragen Sie die Änderungen.
   * Pro Plan:
   * Integration: Korrigieren Sie die Datei selbst und übertragen Sie die Änderungen.
   * Staging und Produktion: Korrigieren Sie die Datei selbst, übertragen Sie die Änderungen und erstellen Sie ein [Adobe Commerce-Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)Ticket, um sie anzuwenden.

1. Aktivieren Sie die Fastly-Bildoptimierung in Commerce Admin (Fastly muss zuvor konfiguriert werden), wie in <https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization> beschrieben.

Wenn die Konfiguration korrekt ist, das Problem jedoch weiterhin auftritt, setzen Sie die Untersuchung fort oder wenden Sie sich an den [Adobe Commerce-Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
