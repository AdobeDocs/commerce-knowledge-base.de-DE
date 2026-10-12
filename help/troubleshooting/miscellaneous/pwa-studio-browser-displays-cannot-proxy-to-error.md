---
title: 'PWA Studio: Der Browser zeigt den Fehler „Proxy nicht möglich für“ an'
description: In diesem Thema wird eine Lösung erläutert, wenn im Webbrowser "*Kein Proxy für*" angezeigt wird und in der Konsole eine
exl-id: de689633-34b8-4a25-bbd0-a58742c4d03c
feature: Console
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%
---
# PWA Studio: Der Browser zeigt den Fehler „Proxy nicht möglich für“ an

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

* [Dokumentation zu PWA Studio für Adobe Commerce](https://developer.adobe.com/commerce/pwa-studio/)
* [Tools und Bibliotheken](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/)
