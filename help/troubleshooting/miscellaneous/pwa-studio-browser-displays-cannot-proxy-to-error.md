---
title: '''PWA Studio: Browser zeigt "Proxy zu Fehler nicht möglich"an'
description: Dieses Thema behandelt eine Lösung, wenn Ihr Webbrowser ein "*Kann nicht Proxy zu"anzeigt und die Konsole ein
exl-id: de689633-34b8-4a25-bbd0-a58742c4d03c
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# PWA Studio: Browser zeigt den Fehler &quot;Proxy zu nicht möglich&quot;an

Dieses Thema behandelt eine Lösung, wenn Ihr Webbrowser eine *Proxy zu*&quot;, zeigt die Konsole eine

```
ENOTFOUND
```

bei Verwendung von Progressive Web App (PWA) Studio für Adobe Commerce.

## Betroffene Produkte und Versionen

* PWA Studio für Adobe Commerce

## Problem

<u>Zu reproduzierende Schritte</u>:

* Laden Sie Ihren Adobe Commerce-Store in einen Browser.

<u>Erwartetes Ergebnis</u>:

* Der Adobe Commerce-Store wird normal in Ihren Browser geladen.

<u>Tatsächliches Ergebnis</u>:

* Ihr Webbrowser zeigt &quot;*Proxy zu*&quot;und die Konsole zeigt einen Fehler wie den folgenden an:

```
    ENOTFOUND
```


## Ursache

NodeJS kann den Hostnamen Ihres Adobe Commerce-Stores nicht auflösen.

## Lösung

1. Stellen Sie sicher, dass Ihr Adobe Commerce Store in mehr als einem Webbrowser geladen wird.
1. Wenn Sie einen lokalen DNS-Server oder VPN ausführen, fügen Sie Ihrer Hostdatei (unter `/etc/hosts`) und ordnen Sie diese Domäne manuell zu ([Allgemeine Anweisungen zur Bearbeitung von Hostdateien](https://linuxize.com/post/how-to-edit-your-hosts-file/)), damit NodeJS es auflösen kann.

## Verwandtes Lesen

* [PWA Studio für die Adobe Commerce-Dokumentation](https://magento.github.io/pwa-studio/)
* [Tools und Bibliotheken](https://magento.github.io/pwa-studio/technologies/tools-libraries/)
