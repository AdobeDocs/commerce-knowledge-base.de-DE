---
title: Adobe Commerce-Bannerausgabe deaktivieren, um die Site-Leistung zu verbessern
description: Dieser Artikel enthält eine Fehlerbehebung für eine niedrige Site-Leistung. Eine niedrige Site-Leistung kann dadurch verursacht werden, dass das Modul "Magento_Banner"aktiviert, aber nicht verwendet wird. Die Deaktivierung der Modulausgabe kann die Site-Leistung verbessern. Überprüfen Sie den Artikel auf Lösungsschritte.
exl-id: 90a8bd21-1f2c-4cfe-8213-17f877e20de8
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Adobe Commerce-Bannerausgabe deaktivieren, um die Site-Leistung zu verbessern

Dieser Artikel enthält eine Fehlerbehebung für eine niedrige Site-Leistung. Eine niedrige Site-Leistung kann dadurch verursacht werden, dass das `Magento_Banner`-Modul aktiviert, aber nicht verwendet wird. Die Deaktivierung der Modulausgabe kann die Site-Leistung verbessern. Überprüfen Sie den Artikel auf Lösungsschritte.

>[!NOTE]
>
>Wenn Sie die Adobe Commerce-Banner-Funktion verwenden, finden Sie im Artikel [Hohe Durchsatzanforderungen AJAX Leistungsanforderungen](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) in unserer Support-Wissensdatenbank Empfehlungen dazu, wie Sie Leistungsprobleme vermeiden können, die durch übermäßige Ajax-Anforderungen verursacht werden.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur v.2.x.x
* Adobe Commerce On-Premise v.2.2.x und 2.3.x

## Problem

Das Modul `Magento_Banner` ist aktiviert, wird jedoch nicht verwendet.

So prüfen Sie, ob dies der Fall ist:

Für Adobe Commerce auf Cloud-Infrastruktur 2.2.x:

1. Melden Sie sich bei Commerce Admin an.
1. Navigieren Sie zu **Inhalt** > *Elemente* > **Banner**.
1. Wenn das auf dieser Seite angezeigte Raster leer ist, haben Sie keine Banner.

Wenn die Option **Banner** unter **Inhalt** > *Elemente* nicht angezeigt wird, ist dies nicht der Fall und die Empfehlungen aus diesem Artikel können nicht angewendet werden.

Für Adobe Commerce in Cloud-Infrastruktur 2.3.x (die Funktion wurde in Version 2.3.x](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/ReleaseNotes2.3.0Commerce.html#banner-now-dynamic-block) um [ umbenannt):

1. Melden Sie sich bei Commerce Admin an.
1. Navigieren Sie zu **Inhalt** > *Elemente >* **Dynamische Blöcke**.
1. Wenn das auf dieser Seite angezeigte Raster leer ist, haben Sie keine dynamischen Blöcke (Banner).

Wenn die Option **Dynamische Blöcke** unter **Inhalt** > *Elemente* nicht angezeigt wird, ist dies nicht der Fall und die Empfehlungen aus diesem Artikel können nicht angewendet werden.

## Ursache

Wenn das Modul `Magento_Banner` aktiviert ist, sendet Adobe Commerce Ajax-Anfragen vom Store an den Server, um die Bannerinformationen zu erhalten. Diese Ajax-Anforderungen wirken sich auf die Leistung aus, insbesondere bei Bedingungen mit hoher Auslastung (hohes Volumen und hohes Traffic). Wenn die Funktion nicht verwendet wird, wird empfohlen, die Modulausgabe zu deaktivieren. Aufgrund der Abhängigkeitsprobleme wird die Deaktivierung des Moduls nicht empfohlen.

## Lösung

>[!WARNING]
>
>Es wird dringend empfohlen, zunächst Änderungen in der [Staging-/Integrationsumgebung](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) zu testen, bevor sie auf die Produktion angewendet werden. Es wird außerdem empfohlen, vor allen Manipulationen ein aktuelles Backup zu erstellen.

1. Deaktivieren Sie die Ausgabe des Moduls `Magento_Banner`, wie in der Entwicklerdokumentation unter [Modulausgabe deaktivieren](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/disable-module-output) beschrieben. Der Modulname, den Sie verwenden müssen, ist `Magento_Banner`.
1. Stellen Sie Ihren Code bereit. Stellen Sie für Adobe Commerce in der Cloud-Infrastruktur wie im Artikel [Bereitstellen Ihres Stores](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production) in unserer Entwicklerdokumentation beschrieben bereit.
