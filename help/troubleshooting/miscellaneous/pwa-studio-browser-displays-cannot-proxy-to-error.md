---
title: 'PWA Studio: Browser zeigt den Fehler "Proxy zu nicht möglich"an'
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

Dieses Thema behandelt eine Lösung, wenn Ihr Webbrowser einen &quot;*Kann nicht auf* proxytieren&quot;anzeigt und die Konsole einen

```
ENOTFOUND
```

bei Verwendung von Progressive Web App (PWA) Studio für Adobe Commerce.

## Betroffene Produkte und Versionen

* PWA Studio für Adobe Commerce

## Problem

<u>Schritt zum Reproduzieren</u>:

* Laden Sie Ihren Adobe Commerce-Store in einen Browser.

<u>Erwartetes Ergebnis</u>:

* Der Adobe Commerce-Store wird normal in Ihren Browser geladen.

<u>Tatsächliches Ergebnis</u>:

* Ihr Webbrowser zeigt den Fehler &quot;*Kann nicht auf*&quot;an und die Konsole zeigt einen Fehler wie den folgenden an:

```
    ENOTFOUND
```


## Ursache

NodeJS kann den Hostnamen Ihres Adobe Commerce-Stores nicht auflösen.

## Lösung

1. Stellen Sie sicher, dass Ihr Adobe Commerce Store in mehr als einem Webbrowser geladen wird.
1. Wenn Sie einen lokalen DNS-Server oder VPN ausführen, fügen Sie Ihrer Hostdatei (in `/etc/hosts`) einen Eintrag hinzu und ordnen Sie diese Domäne manuell zu ([Allgemeine Anweisungen zur Bearbeitung von Hostdateien](https://linuxize.com/post/how-to-edit-your-hosts-file/)), sodass NodeJS sie auflösen kann.

## Verwandtes Lesen

* [PWA Studio für Adobe Commerce-Dokumentation](https://magento.github.io/pwa-studio/)
* [Tools und Bibliotheken](https://magento.github.io/pwa-studio/technologies/tools-libraries/)
