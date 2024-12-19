---
title: Fehler beim Löschen des Fastly-Cache in der Cloud (die Löschanfrage wurde nicht erfolgreich verarbeitet)
description: 'Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass Sie eine Schnellbereinigungsoption verwenden und die folgende Fehlermeldung erhalten: *Die Bereinigungsanfrage wurde nicht erfolgreich verarbeitet*. Fastly ist ein CDN- und Caching-Service, der in Adobe Commerce zu Cloud-Infrastrukturplänen und -Implementierungen enthalten ist. Wenn Sie versuchen, eine Fastly-Bereinigungsoption zu verwenden, die nicht verarbeitet wird, haben Sie möglicherweise falsche Fastly-Anmeldeinformationen in Ihrer Umgebung oder es ist ein Problem aufgetreten.'
exl-id: 568b1f4c-2ccb-4740-a6e4-d227a55fcfe6
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Fehler beim Löschen des Fastly-Cache in der Cloud (die Löschanfrage wurde nicht erfolgreich verarbeitet)

Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass Sie eine Schnellbereinigungsoption verwenden und die folgende Fehlermeldung erhalten: *Die Bereinigungsanfrage wurde nicht erfolgreich verarbeitet*. Fastly ist ein CDN- und Caching-Service, der in Adobe Commerce zu Cloud-Infrastrukturplänen und -Implementierungen enthalten ist. Wenn Sie versuchen, eine Fastly-Bereinigungsoption zu verwenden, die nicht verarbeitet wird, haben Sie möglicherweise falsche Fastly-Anmeldeinformationen in Ihrer Umgebung oder es ist ein Problem aufgetreten.

Diese Informationen helfen Ihnen beim Überprüfen und Testen von Fastly-Kopfzeilen für Ihre Live-Site und Ihre Ursprungs-Server.

## Betroffene Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.1.x und höher
* Fastly 1.2.27 und höher

## Problem

Das Caching funktioniert, aber wenn Sie versuchen, zu bereinigen, erhalten Sie einen Fehler oder es funktioniert nicht. Der Fehler umfasst: „Die Bereinigungsanfrage wurde nicht erfolgreich verarbeitet.“

## Ursache

Möglicherweise sind in Ihrer Umgebung falsche Anmeldeinformationen festgelegt oder Sie müssen VCL-Snippets hochladen.

## Lösen

### Anmeldedaten von Fastly überprüfen

Überprüfen Sie, ob Sie die richtige Fastly Service-ID und das richtige API-Token in Ihrer Umgebung haben. Wenn Sie in der Produktionsumgebung über Staging-Anmeldedaten verfügen, werden die Bereinigungen möglicherweise nicht richtig verarbeitet oder verarbeitet.

1. Melden Sie sich bei Ihrem lokalen Commerce-Administrator als Administrator an.
1. Klicken Sie auf **Stores** > Einstellungen > **Konfiguration** > **Erweitert** > **System** und erweitern Sie **Vollständiger Seitencache**.    ![magento_full_page_cache_2.4.1.png](assets/magento_full_page_cache_2.4.1.png)
1. Erweitern Sie Fastly Configuration und überprüfen Sie die Fastly Service-ID und das API-Token für Ihre Umgebung.
1. Wenn Sie die Werte ändern, klicken Sie auf Testanmeldedaten.

### VCL-Snippets überprüfen

Wenn die Anmeldeinformationen korrekt sind, können Probleme mit Ihren VCLs auftreten. Um Ihre VCLs pro Service aufzulisten und zu überprüfen, geben Sie den folgenden API-Aufruf in einem Terminal ein:

```
curl -X GET -s https://api.fastly.com/service/<Service ID>/version/<Editable Version #>/snippet -H "Fastly-Key:FASTLY_API_TOKEN"
```

Überprüfen Sie die Liste der VCLs. Wenn Sie Probleme mit den Standard-VCLs von Fastly haben, können Sie den Inhalt erneut hochladen oder gemäß den [Fastly Standard-VCLs) ](https://github.com/fastly/fastly-magento2/tree/master/etc/vcl_snippets). Informationen zum Bearbeiten Ihrer benutzerdefinierten VCLs finden Sie unter [Benutzerdefinierte Fastly-VCL-Snippets](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) im Handbuch zu Commerce in Cloud Infrastructure.

## Weitere Informationen

In unserer Entwicklerdokumentation:

* [Über Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)
* [Schnell einrichten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)
* [Benutzerdefinierte Fastly VCL-Snippets](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html)
