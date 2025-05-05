---
title: 'Adobe Commerce On-Premises 2.4.2: Produktimage fehlt'
description: In diesem Artikel wird ein bekanntes Adobe Commerce On-Premises 2.4.2-Problem beschrieben, bei dem das Produktbild nicht auf die Produktseite hochgeladen wird. Dieses Problem soll in einer zukünftigen Version nach Version 2.4.3 behoben werden. Derzeit ist keine Lösung verfügbar, aber Sie können Nginx deaktivieren, um die Größe von Bildern zu ändern.
exl-id: c4d9240e-5df5-4eab-bb4e-1f06f9bd3a1e
feature: Iaas, Products, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Adobe Commerce On-Premises 2.4.2: Produktimage fehlt

In diesem Artikel wird ein bekanntes Adobe Commerce On-Premises 2.4.2-Problem beschrieben, bei dem das Produktbild nicht auf die Produktseite hochgeladen wird. Dieses Problem soll in einer zukünftigen Version nach Version 2.4.3 behoben werden. Derzeit ist keine Lösung verfügbar, aber Sie können Nginx deaktivieren, um die Größe von Bildern zu ändern.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.4.2

## Problem

Das Produktbild wird im `s3`-Bucket gespeichert, es wird jedoch nicht mit dem `pub/media` synchronisiert. Dieses Problem tritt nur auf, wenn beide verwendet werden:

* Site-aktiviertes Nginx zum Ändern der Bildgröße
* AWS `s3` als Medienspeicher

<u>Voraussetzungen</u>:

Adobe Commerce mit Nginx installiert.

<u>Schritte zur Reproduktion</u>:

1. Konfigurieren Sie Adobe Commerce für die Verwendung von AWS `s3` als Medienspeicher.
1. Konfigurieren Sie Nginx mithilfe der `nginx.conf.sample` Konfigurationsdatei im Adobe Commerce-Installationsverzeichnis und einem virtuellen Nginx-Host. Siehe [Konfigurieren von ](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/prerequisites/web-server/nginx)&quot; in unserer Entwicklerdokumentation.
1. Erstellen Sie ein einfaches Produkt mit einem Produktbild.
1. Nginx hat eine unkommentierte Konfiguration für die Größenänderung von Bildern in `nginx.conf.sample`, die etwa wie folgt aussieht:

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

## Abhilfe

Deaktivieren Sie Nginx, um die Bildgröße zu ändern.
