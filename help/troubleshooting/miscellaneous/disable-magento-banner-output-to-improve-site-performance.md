---
title: Adobe Commerce-Bannerausgabe deaktivieren, um die Site-Leistung zu verbessern
description: Dieser Artikel enthält eine Fehlerbehebung für eine niedrige Site-Leistung. Eine niedrige Site-Leistung kann dadurch verursacht werden, dass das Modul "Magento_Banner"aktiviert, aber nicht verwendet wird. Die Deaktivierung der Modulausgabe kann die Site-Leistung verbessern. Überprüfen Sie den Artikel auf Lösungsschritte.
exl-id: 90a8bd21-1f2c-4cfe-8213-17f877e20de8
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Adobe Commerce-Bannerausgabe deaktivieren, um die Site-Leistung zu verbessern

Dieser Artikel enthält eine Fehlerbehebung für eine niedrige Site-Leistung. Eine niedrige Site-Leistung kann durch die `Magento_Banner` -Modul aktiviert, aber nicht verwendet. Die Deaktivierung der Modulausgabe kann die Site-Leistung verbessern. Überprüfen Sie den Artikel auf Lösungsschritte.

>[!NOTE]
>
>Wenn Sie die Adobe Commerce Banner-Funktion verwenden, lesen Sie die Informationen unter [Hohe Durchsatzraten AJAX Anforderungen führen zu schlechter Leistung](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) in unserer Support-Wissensdatenbank finden Sie Empfehlungen, wie Sie Leistungsprobleme vermeiden können, die durch übermäßige Ajax-Anforderungen verursacht werden.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur v.2.x.x
* Adobe Commerce On-Premise v.2.2.x und 2.3.x

## Problem

Die `Magento_Banner` -Modul aktiviert ist, aber nicht verwendet.

So prüfen Sie, ob dies der Fall ist:

Für Adobe Commerce auf Cloud-Infrastruktur 2.2.x:

1. Melden Sie sich bei Commerce Admin an.
1. Navigieren Sie zu **Inhalt** > *Elemente* > **Banner**.
1. Wenn das auf dieser Seite angezeigte Raster leer ist, haben Sie keine Banner.

Wenn die Variable **Banner** Option unter **Inhalt** > *Elemente*, ist dies nicht der Fall und die Empfehlungen aus diesem Artikel können nicht angewendet werden.

Für Adobe Commerce in der Cloud-Infrastruktur 2.3.x (Funktionalität: [in Version 2.3.x umbenannt.](https://devdocs.magento.com/guides/v2.3/release-notes/ReleaseNotes2.3.0Commerce.html#banner-now-dynamic-block)):

1. Melden Sie sich bei Commerce Admin an.
1. Navigieren Sie zu **Inhalt** > *Elemente >*  **Dynamische Blöcke**.
1. Wenn das auf dieser Seite angezeigte Raster leer ist, haben Sie keine dynamischen Blöcke (Banner).

Wenn die Variable **Dynamische Blöcke** Option unter **Inhalt** > *Elemente*, ist dies nicht der Fall und die Empfehlungen aus diesem Artikel können nicht angewendet werden.

## Ursache

Wenn die Variable `Magento_Banner` aktiviert ist, sendet Adobe Commerce Ajax-Anfragen vom Store an den Server, um die Bannerinformationen zu erhalten. Diese Ajax-Anforderungen wirken sich auf die Leistung aus, insbesondere bei Bedingungen mit hoher Auslastung (hohes Volumen und hohes Traffic). Wenn die Funktion nicht verwendet wird, wird empfohlen, die Modulausgabe zu deaktivieren. Aufgrund der Abhängigkeitsprobleme wird die Deaktivierung des Moduls nicht empfohlen.

## Lösung

>[!WARNING]
>
>Wir empfehlen dringend, Änderungen an [Staging-/Integrationsumgebung](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) zuerst, bevor sie auf die Produktion angewendet wird. Es wird außerdem empfohlen, vor allen Manipulationen ein aktuelles Backup zu erstellen.

1. Deaktivieren Sie die `Magento_Banner` Modulausgabe, wie unter [Modulausgabe deaktivieren](https://devdocs.magento.com/guides/v2.3/config-guide/config/disable-module-output.html) in unserer Entwicklerdokumentation. Der Name des Moduls, das Sie verwenden müssen, lautet `Magento_Banner`.
1. Stellen Sie Ihren Code bereit. Stellen Sie für Adobe Commerce in der Cloud-Infrastruktur wie im Abschnitt [Bereitstellen Ihres Stores](https://devdocs.magento.com/guides/v2.3/cloud/live/stage-prod-live.html) in unserer Entwicklerdokumentation.
