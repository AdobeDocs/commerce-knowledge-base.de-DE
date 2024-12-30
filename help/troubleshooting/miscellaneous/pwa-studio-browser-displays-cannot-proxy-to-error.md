---
title: 'PWA Studio: Der Browser zeigt den Fehler „Proxy kann nicht verwendet werden“ an'
description: In diesem Thema wird eine Lösung erläutert, wenn im Webbrowser "*Kein Proxy für*" angezeigt wird und in der Konsole eine
exl-id: de689633-34b8-4a25-bbd0-a58742c4d03c
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# PWA Studio: Der Browser zeigt den Fehler „Proxy kann nicht verwendet werden“ an

In diesem Thema wird eine Lösung erläutert, wenn im Webbrowser &quot;*Proxy für nicht möglich“* und in der Konsole eine

```
ENOTFOUND
```

Fehler bei Verwendung von Progressive Web App (PWA) Studio für Adobe Commerce.

## Betroffene Produkte und Versionen

* PWA Studio für Adobe Commerce

## Problem

<u>Schritt zur Reproduktion</u>:

* Laden Sie Ihren Adobe Commerce-Store in einem Browser.

<u>Erwartetes Ergebnis</u>:

* Der Adobe Commerce-Store wird normal in Ihrem Browser geladen.

<u>Tatsächliches </u>:

* Ihr Webbrowser zeigt den Fehler &quot;*kann keinen Proxy für* erstellen“ und die Konsole zeigt einen Fehler wie den folgenden an:

```
    ENOTFOUND
```


## Ursache

NodeJS kann den Hostnamen Ihres Adobe Commerce-Stores nicht auflösen.

## Lösung

1. Stellen Sie sicher, dass Ihr Adobe Commerce-Store in mehr als einem Webbrowser geladen wird.
1. Wenn Sie einen lokalen DNS-Server oder ein VPN ausführen, fügen Sie der Hostdatei (in `/etc/hosts`) einen Eintrag hinzu und ordnen Sie diese Domain manuell zu ([Allgemeine Anweisungen zur Bearbeitung von Hostdateien](https://linuxize.com/post/how-to-edit-your-hosts-file/)), damit NodeJS sie auflösen kann.

## Verwandtes Lesen

* Dokumentation zu [PWA Studio für Adobe Commerce](https://magento.github.io/pwa-studio/)
* [Tools und Bibliotheken](https://magento.github.io/pwa-studio/technologies/tools-libraries/)
