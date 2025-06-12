---
title: Adobe Commerce-Bannerausgabe deaktivieren, um die Site-Leistung zu verbessern
description: Dieser Artikel bietet eine Fehlerbehebung für die geringe Site-Leistung. Eine geringe Site-Performance kann dadurch verursacht werden, dass das Modul "Magento_Banner“ aktiviert, aber nicht verwendet wird. Durch Deaktivieren der Modulausgabe kann die Site-Leistung verbessert werden. Lesen Sie den Artikel zu den Schritten zur Problembehebung.
exl-id: 90a8bd21-1f2c-4cfe-8213-17f877e20de8
feature: Configuration
role: Developer
source-git-commit: 76ef59dc37504f50d55734a90c9ce5b30bb83175
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Adobe Commerce-Bannerausgabe deaktivieren, um die Site-Leistung zu verbessern

Dieser Artikel bietet eine Fehlerbehebung für die geringe Site-Leistung. Eine niedrige Site-Leistung kann dadurch verursacht werden, dass das `Magento_Banner`-Modul aktiviert, aber nicht verwendet wird. Durch Deaktivieren der Modulausgabe kann die Site-Leistung verbessert werden. Lesen Sie den Artikel zu den Schritten zur Problembehebung.

>[!NOTE]
>
>Wenn Sie die Adobe Commerce-Bannerfunktion verwenden, finden Sie im Artikel [AJAX-Anfragen mit hohem Durchsatz verursachen schlechte Leistung](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) in unserer Support-Wissensdatenbank Empfehlungen, wie Sie Leistungsprobleme vermeiden können, die durch übermäßige Ajax-Anfragen verursacht werden.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur v.2.x.x
* Adobe Commerce On-Premises v.2.2.x und 2.3.x

## Problem

Das `Magento_Banner` ist aktiviert, wird aber nicht verwendet.

So überprüfen Sie, ob dies der Fall ist:

Für Adobe Commerce auf Cloud-Infrastruktur 2.2.x:

1. Melden Sie sich beim Commerce Admin an.
1. Navigieren Sie zu **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Banners]**.
1. Wenn das auf dieser Seite angezeigte Raster leer ist, haben Sie keine Banner.

Wenn die Option **[!UICONTROL Banners]** unter **[!UICONTROL Content]** > **[!UICONTROL Elements]** nicht angezeigt wird, bedeutet dies, dass Sie die Empfehlungen aus diesem Artikel bereits angewendet haben.

Für Adobe Commerce auf Cloud-Infrastrukturen 2.3.x und höher (die Funktion wurde [in Version 2.3.x umbenannt](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/ReleaseNotes2.3.0Commerce.html#banner-now-dynamic-block)):

1. Melden Sie sich beim Commerce Admin an.
1. Navigieren Sie zu **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Dynamic Blocks]**.
1. Wenn das auf dieser Seite angezeigte Raster leer ist, verfügen Sie über keine dynamischen Blöcke (Banner).

Wenn die **[!UICONTROL Dynamic Blocks]** Option unter **[!UICONTROL Content]** > **[!UICONTROL Elements]** nicht angezeigt wird, bedeutet dies, dass Sie die Empfehlung aus diesem Artikel bereits angewendet haben. Um die Banneroption erneut anzuzeigen, kehren Sie den Vorgang um.

## Ursache

Wenn das `Magento_Banner` aktiviert ist, sendet Adobe Commerce Ajax-Anfragen von der Storefront an den Server, um die Bannerinformationen abzurufen. Diese Ajax-Anfragen wirken sich auf die Leistung aus, insbesondere unter Bedingungen mit hoher Last (hohes Volumen und hohes Traffic). Wenn die Funktion nicht verwendet wird, wird empfohlen, die Modulausgabe zu deaktivieren. Aufgrund von Abhängigkeitsproblemen wird nicht empfohlen, das Modul zu deaktivieren.

## Lösung

>[!WARNING]
>
>Es wird dringend empfohlen, Änderungen zunächst in [Staging-/Integrationsumgebung](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) zu testen, bevor sie auf die Produktion angewendet werden. Wir empfehlen auch, vor jeder Manipulation ein aktuelles Backup zu haben.

1. Deaktivieren Sie die Ausgabe des `Magento_Banner`, wie unter [Modulausgabe deaktivieren](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/files/disable-module-output) in unserer Entwicklerdokumentation beschrieben. Der Modulname, den Sie verwenden müssen, lautet `Magento_Banner`.
1. Bereitstellen des Codes. Stellen Sie für Adobe Commerce in der Cloud-Infrastruktur bereit, wie im Artikel [Bereitstellen Ihres Stores](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production) in unserer Entwicklerdokumentation beschrieben.
1. Nach Deaktivierung der Modulausgabe erscheint das Menü nicht mehr in der Admin-Liste.
1. Unter **[!UICONTROL Content]** > **[!UICONTROL Elements]** werden das Banner oder die dynamische Option nicht mehr angezeigt. Um die Optionen wieder anzuzeigen, [aktivieren Sie die Modulausgabe](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/files/disable-module-output?lang=en#disable-module-output-in-a-simple-deployment).

