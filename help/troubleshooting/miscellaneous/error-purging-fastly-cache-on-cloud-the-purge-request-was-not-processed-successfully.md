---
title: Fehler beim Bereinigen des Fastly-Cache in Cloud (Die Bereinigungsanforderung wurde nicht erfolgreich verarbeitet)
description: '''Dieser Artikel enthält eine Korrektur für den Fall, dass Sie eine Option zur schnellen Bereinigung verwenden und den Fehler erhalten: *Die Bereinigungsanfrage wurde nicht erfolgreich verarbeitet*. Fastly ist ein CDN- und Caching-Dienst, der in Adobe Commerce in Cloud-Infrastrukturplänen und -Implementierungen enthalten ist. Wenn Sie versuchen, eine Option zur schnellen Bereinigung zu verwenden, die nicht verarbeitet wird, liegen möglicherweise falsche Anmeldeinformationen in Ihrer Umgebung vor oder es ist möglicherweise ein Problem aufgetreten."'
exl-id: 568b1f4c-2ccb-4740-a6e4-d227a55fcfe6
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Fehler beim Bereinigen des Fastly-Cache in Cloud (Die Bereinigungsanforderung wurde nicht erfolgreich verarbeitet)

Dieser Artikel enthält eine Fehlerbehebung für die Verwendung der Option Schnelle Bereinigung und Sie erhalten den Fehler: *Die Bereinigungsanforderung wurde nicht erfolgreich verarbeitet*. Fastly ist ein CDN- und Caching-Dienst, der in Adobe Commerce in Cloud-Infrastrukturplänen und -Implementierungen enthalten ist. Wenn Sie versuchen, eine Option zur schnellen Bereinigung zu verwenden, die nicht verarbeitet wird, liegen möglicherweise falsche Anmeldeinformationen in Ihrer Umgebung vor oder es ist ein Problem aufgetreten.

Diese Informationen helfen Ihnen beim Überprüfen und Testen von Schnellkopfzeilen für Ihre Live-Site und Herkunftsserver.

## Betroffene Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.1.X und höher
* Fastly 1.2.27 und höher

## Problem

Das Caching funktioniert zwar, aber wenn Sie versuchen zu bereinigen, erhalten Sie einen Fehler oder es funktioniert nicht. Der Fehler enthält: &quot;Die Bereinigungsanforderung wurde nicht erfolgreich verarbeitet.&quot;

## Ursache

Möglicherweise haben Sie in Ihrer Umgebung falsche Anmeldeinformationen festgelegt oder müssen VCL-Snippets hochladen.

## Auflösen

### Fastly-Anmeldeinformationen überprüfen

Überprüfen Sie, ob Sie in Ihrer Umgebung über die richtige Fastly Service-ID und das richtige API-Token verfügen. Wenn Sie über Staging-Anmeldeinformationen in der Produktion verfügen, werden die Bereinigungen möglicherweise nicht korrekt verarbeitet oder verarbeitet.

1. Melden Sie sich bei Ihrem lokalen Commerce-Administrator als Administrator an.
1. Klicks **Stores** > Einstellungen > **Konfiguration** > **Erweitert** > **System** und erweitern **Vollständiger Seiten-Cache**.    ![magento_full_page_cache_2.4.1.png](assets/magento_full_page_cache_2.4.1.png)
1. Erweitern Sie Fastly Configuration und überprüfen Sie die Fastly Service-ID und das API-Token für Ihre Umgebung.
1. Wenn Sie die Werte ändern, klicken Sie auf Testanmeldeinformationen.

### VCL-Snippets überprüfen

Wenn die Anmeldedaten korrekt sind, kann es bei Ihnen zu Problemen mit Ihren VCLs kommen. Um Ihre VCLs pro Dienst aufzulisten und zu überprüfen, geben Sie den folgenden API-Aufruf in ein Terminal ein:

```
curl -X GET -s https://api.fastly.com/service/<Service ID>/version/<Editable Version #>/snippet -H "Fastly-Key:FASTLY_API_TOKEN"
```

Überprüfen Sie die Liste der VCL. Wenn Sie Probleme mit den standardmäßigen VCLs von Fastly haben, können Sie den Inhalt erneut hochladen oder überprüfen. [Fastly default VCLs](https://github.com/fastly/fastly-magento2/tree/master/etc/vcl_snippets). Informationen zum Bearbeiten Ihrer benutzerdefinierten VCLs finden Sie unter [Benutzerdefinierte Fastly VCL-Snippets](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) im Commerce on Cloud Infrastructure Guide.

## Weitere Informationen

In unserer Entwicklerdokumentation:

* [Über Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)
* [Schnelles Einrichten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)
* [Benutzerdefinierte Fastly VCL-Snippets](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html)
