---
title: Bilder speichern, die nach der Bereitstellung nicht angezeigt werden
description: Dieser Artikel bietet eine Lösung für Fälle, in denen Bilder nach der Bereitstellung nicht korrekt angezeigt werden.
exl-id: 7e6bcebd-edff-437a-9103-2743443d2ed9
feature: Cache, Categories, Deploy, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---

# Bilder speichern, die nach der Bereitstellung nicht angezeigt werden

Dieser Artikel bietet eine Lösung für Fälle, in denen Bilder nach der Bereitstellung nicht korrekt angezeigt werden.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x

## Problem

Wenn Sie ein Storefront-Design mit einer Bildgrößenanpassung verwenden, werden die Bilder bei der Bereitstellung nicht auf den Katalogseiten angezeigt oder verschwinden nicht.

## Ursache

Dies kann durch Laden der Bilder aus dem Cache verursacht werden.

## Lösung

In diesem Fall können Sie den Befehl Magento verwenden, um den Bildcache neu zu generieren und die Bilder korrekt anzuzeigen.

Dazu benötigen Sie die SSH-Informationen und die Store-URL, die über die [Cloud-Konsole“ verfügbar ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html).

1. SSH zu Ihrem Projekt, das eine Quelle für den [Datenbank-Dump](/help/how-to/general/create-database-dump-on-cloud.md) war, wie unter [SSH in ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) in unserer Entwicklerdokumentation beschrieben.
1. Generieren Sie den Bild-Cache neu, indem Sie Folgendes ausführen:

   ```bash
   php bin/magento catalog:images:resize
   ```

1. Testen Sie die Kategorieseiten über die Store-URL.
