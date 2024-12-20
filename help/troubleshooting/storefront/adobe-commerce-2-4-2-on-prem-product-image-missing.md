---
title: 'Adobe Commerce vor Ort 2.4.2: Produktbild fehlt'
description: In diesem Artikel wird ein bekanntes Problem mit Adobe Commerce On-Premise 2.4.2 beschrieben, bei dem das Produktbild nicht auf die Produktseite hochgeladen wird. Dieses Problem soll in einer zukünftigen Version nach Version 2.4.3 behoben werden. Derzeit ist keine Lösung verfügbar, aber als Problemumgehung können Sie Nginx deaktivieren, um die Bildgröße zu ändern.
exl-id: c4d9240e-5df5-4eab-bb4e-1f06f9bd3a1e
feature: Iaas, Products, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Adobe Commerce vor Ort 2.4.2: Produktbild fehlt

In diesem Artikel wird ein bekanntes Problem mit Adobe Commerce On-Premise 2.4.2 beschrieben, bei dem das Produktbild nicht auf die Produktseite hochgeladen wird. Dieses Problem soll in einer zukünftigen Version nach Version 2.4.3 behoben werden. Derzeit ist keine Lösung verfügbar, aber als Problemumgehung können Sie Nginx deaktivieren, um die Bildgröße zu ändern.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.4.2

## Problem

Das Produktbild wird im Bucket `s3` gespeichert, aber nicht wieder mit dem Verzeichnis `pub/media` synchronisiert. Dieses Problem tritt nur bei Verwendung von beidem auf:

* Site-aktivierter Nginx zur Größenanpassung von Bildern
* AWS `s3` als Medienspeicher

<u>Voraussetzungen</u>:

Adobe Commerce wird mit Nginx installiert.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie Adobe Commerce für die Verwendung von AWS `s3` als Medienspeicher.
1. Konfigurieren Sie Nginx mithilfe der Konfigurationsdatei &quot;`nginx.conf.sample`&quot;, die im Adobe Commerce-Installationsverzeichnis bereitgestellt wird, und eines virtuellen Nginx-Hosts. Siehe [Konfigurieren von Nginx](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/web-server/nginx) in unserer Entwicklerdokumentation.
1. Erstellen Sie ein einfaches Produkt mit einem Produktbild.
1. Nginx verfügt über eine nicht kommentierte Konfiguration für die Bildgröße in `nginx.conf.sample`, die der folgenden ähnelt:

```conf
load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
location /media/ {
    location ~* ^/media/catalog/.* {
        set $width "-";
        set $height "-";
        if ($arg_width != '') {
            set $width $arg_width;
        }
        if ($arg_height != '') {
            set $height $arg_height;
        }
        image_filter resize $width $height;
        image_filter_jpeg_quality 90;
    }
```

<u>Erwartete Ergebnisse</u>:

Das Produktbild wird auf die Produktseite hochgeladen.

<u>Tatsächliche Ergebnisse</u>:

Das Produktbild wird nicht auf die Produktseite hochgeladen.

## Workaround

Deaktivieren Sie Nginx, um die Bildgröße zu ändern.
