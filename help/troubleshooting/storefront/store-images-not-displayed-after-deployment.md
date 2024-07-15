---
title: Store-Bilder werden nach der Implementierung nicht angezeigt
description: Dieser Artikel bietet eine Lösung für Fälle, in denen Bilder nach der Bereitstellung nicht korrekt angezeigt werden.
exl-id: 7e6bcebd-edff-437a-9103-2743443d2ed9
feature: Cache, Categories, Deploy, Storefront
role: Admin
source-git-commit: c4d586ca3980acbe4f33c5f2616ef7f3051bc7d3
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---

# Store-Bilder werden nach der Implementierung nicht angezeigt

Dieser Artikel bietet eine Lösung für Fälle, in denen Bilder nach der Bereitstellung nicht korrekt angezeigt werden.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x

## Problem

Wenn Sie ein Storefront-Design mit einer Bildgröße verwenden, werden die Bilder bei der Bereitstellung nicht auf den Katalogseiten angezeigt oder verschwinden.

## Ursache

Dies kann durch das Laden der Bilder aus dem Cache geschehen.

## Lösung

In diesem Fall können Sie den Magento-Befehl verwenden, um den Bild-Cache neu zu generieren und die Bilder korrekt anzuzeigen.

Dazu benötigen Sie die SSH-Informationen und die Store-URL, die über die [Cloud-Konsole](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html) verfügbar sind.

1. SSH zu Ihrem Projekt, das eine Quelle für den [Datenbank-Dump](/help/how-to/general/create-database-dump-on-cloud.md) war, wie in der Entwicklerdokumentation unter [SSH in die Umgebung](https://devdocs.magento.com/guides/v2.3/cloud/env/environments-ssh.html#ssh) beschrieben.
1. Regenerieren Sie den Bild-Cache, indem Sie Folgendes ausführen:

   ```bash
   php bin/magento catalog:images:resize
   ```

1. Testen Sie die Kategorieseiten über die Store-URL.
