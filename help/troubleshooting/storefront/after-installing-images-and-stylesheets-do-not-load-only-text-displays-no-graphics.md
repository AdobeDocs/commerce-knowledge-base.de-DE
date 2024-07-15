---
title: Nach der Installation werden keine Bilder und Stylesheets geladen. Nur Text wird angezeigt, keine Grafiken
description: In diesem Artikel werden die möglichen Gründe und Lösungen für das Problem beschrieben, dass Stylesheets und Bilder nach der Installation von Adobe Commerce nicht geladen werden.
exl-id: f33cee89-b416-4d63-8cc5-9cc57618ce92
feature: Install, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# Nach der Installation werden keine Bilder und Stylesheets geladen. Nur Text wird angezeigt, keine Grafiken

In diesem Artikel werden die möglichen Gründe und Lösungen für das Problem beschrieben, dass Stylesheets und Bilder nach der Installation von Adobe Commerce nicht geladen werden.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Problem

<u>Zu reproduzierende Schritte</u>

1. Installieren Sie Adobe Commerce.
1. Navigieren Sie zur Storefront oder zum Administrator.

<u>Erwartetes Ergebnis</u>

Stile werden angewendet, kein UI-Element sieht aus wie fehlende Stile.

<u>Tatsächliches Ergebnis</u>

Stile werden nicht korrekt angewendet, Grafiken fehlen.

## Ursache

Der Pfad zu Bildern und Stylesheets ist nicht korrekt, entweder aufgrund einer falschen Basis-URL oder weil Server-Neuschreibungen (CentOS, Ubuntu) nicht ordnungsgemäß eingerichtet sind.

Um dies zu bestätigen, verwenden Sie einen Webbrowser-Inspektor, um die Pfade zu statischen Assets zu überprüfen und sicherzustellen, dass sich diese Assets im Dateisystem von Adobe Commerce oder Magento Open Source befinden.

Statische Assets befinden sich unter `<magento_root>/pub/static/` in den Verzeichnissen `frontend` und `adminhtml` .

## Lösung

Die folgenden Lösungen sind je nach verwendeter Software und Ursache des Problems möglich:

* Wenn Sie den Apache-Webserver verwenden, überprüfen Sie Ihre Einstellung [server rewrites](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/apache.html#apache-help-rewrite) und die Basis-URL Ihres Adobe Commerce-/Magento Open Source-Servers und versuchen Sie es erneut. Wenn Sie die Apache `AllowOverride`-Direktive falsch eingerichtet haben, werden die statischen Dateien nicht vom richtigen Speicherort bereitgestellt.
* Wenn Sie den nginx-Webserver verwenden, stellen Sie sicher, dass Sie [eine virtuelle Host-Datei konfigurieren](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/nginx.html#configure-nginx-ubuntu). Die nginx-Virtual-Host-Datei muss die folgenden Kriterien erfüllen:
   * Die Anweisung `include` muss auf die Beispielkonfigurationsdatei nginx im Installationsverzeichnis von Adobe Commerce/Magento Open Source verweisen. Beispiel:    `include /var/www/html/magento2/nginx.conf.sample;`
   * Die Anweisung `server_name` muss mit der Basis-URL übereinstimmen, die Sie bei der Installation von Adobe Commerce/Magento Open Source angegeben haben. Beispiel: `server_name 192.186.33.10;`
* Wenn sich die Anwendung im [Produktionsmodus ](https://devdocs.magento.com/guides/v2.3/config-guide/bootstrap/magento-modes.html#production-mode) befindet, versuchen Sie, statische Ansichtsdateien mit dem Befehl `magento setup:static-content:deploy` bereitzustellen. Weitere Informationen zur Bereitstellung statischer Dateien finden Sie unter [Statische Ansichtsdateien bereitstellen](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-maint.html) in unserer Entwicklerdokumentation.
