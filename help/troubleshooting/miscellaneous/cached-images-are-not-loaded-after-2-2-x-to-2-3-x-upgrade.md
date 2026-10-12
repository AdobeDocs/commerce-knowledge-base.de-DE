---
title: Zwischengespeicherte Bilder werden nach dem Upgrade von 2.2.x auf 2.3.x nicht geladen
description: Dieser Artikel bietet die Lösung für das Problem, dass zwischengespeicherte Bilder nach dem Upgrade von Adobe Commerce auf Cloud-Infrastruktur 2.2.x auf 2.3.x nicht angezeigt werden.
exl-id: 3e6bd5aa-bd5d-4880-8b78-64f280647abe
feature: Cache, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '287'
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
   * Staging und Produktion: Korrigieren Sie die Datei selbst, übertragen Sie die Änderungen und erstellen Sie ein [Adobe Commerce-Support](https://experienceleague.adobe.com/de/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide)Ticket, um sie anzuwenden.

1. Aktivieren Sie die Fastly-Bildoptimierung in Commerce Admin (Fastly muss zuvor konfiguriert werden), wie in <https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization> beschrieben.

Wenn die Konfiguration korrekt ist, das Problem jedoch weiterhin auftritt, setzen Sie die Untersuchung fort oder wenden Sie sich an den [Adobe Commerce-Support](https://experienceleague.adobe.com/de/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide).
