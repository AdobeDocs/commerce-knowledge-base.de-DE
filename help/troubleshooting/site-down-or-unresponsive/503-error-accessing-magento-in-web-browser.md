---
title: 503-Fehler beim Zugriff auf Adobe Commerce im Webbrowser
description: Dieser Artikel bietet eine mögliche Lösung für das Problem, dass beim Zugriff auf Adobe Commerce Storefront und/oder Admin ein 503-Fehler auftritt.
exl-id: 4232aa21-40c2-41b0-9fb0-fc8cd4db8e39
feature: Storefront
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# 503-Fehler beim Zugriff auf Adobe Commerce im Webbrowser

Dieser Artikel bietet eine mögliche Lösung für das Problem, dass beim Zugriff auf Adobe Commerce Storefront und/oder Admin ein 503-Fehler auftritt.

## Betroffene Produkte und Versionen

Adobe Commerce 2.3.x

## Problem {#symptoms}

<u>Zu reproduzierende Schritte</u>

(Voraussetzungen: Stellen Sie sicher, dass der Store nicht in [Wartungsmodus](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-mode.html#config-mode-show)).

Navigieren Sie in einem Webbrowser zu Ihrem Commerce-Administrator oder Ihrer Storefront.

<u>Erwartetes Ergebnis</u>

Die Seite wird geladen.

<u>Tatsächliches Ergebnis</u>

Sie erhalten den Fehler HTTP 503 (Dienst nicht verfügbar). Der Apache `error.log` enthält die folgende Meldung:

*Ungültiger Befehl &#39;Bestellung&#39;, möglicherweise falsch geschrieben oder von einem Modul definiert, das nicht in der Serverkonfiguration enthalten ist.*

## Ursache {#details}

Apache 2.4-Kompatibilitätsmodul `mod_access_compat` deaktiviert ist, was dazu führt, dass Adobe Commerce-URL-Neuschreibungen nicht ordnungsgemäß funktionieren.

## Lösung {#suggested-solution}

Aktivieren Sie die `mod_access_compat` Apache-Modul verwenden und Apache neu starten, indem Sie Folgendes als Benutzer mit &quot;root&quot;-Berechtigungen ausführen:

```bash
a2enmod access_compat
service <name> restart
```

Unter CentOS:

```bash
<name>
```

is

```bash
httpd
```

. Ubuntu:

```bash
<name>
```

is

```bash
apache2
```

.

## Verwandtes Lesen {#additional-resources}

* [Apache-Dokumentation zu mod\_access\_compat](https://httpd.apache.org/docs/current/mod/mod_access_compat.html)
* [Apache-Dokumentation zu mod\_authz\_host](https://httpd.apache.org/docs/current/mod/mod_authz_host.html)
* [Sortieren, Zulassen, Ablehnen aus dem Apache-Definitionshandbuch](https://docstore.mik.ua/orelly/linux/apache/ch05_06.htm)
* [askubuntu.com](https://askubuntu.com/questions/335228/changes-in-apache-config-between-12-04-2-and-12-04-3-lts)
