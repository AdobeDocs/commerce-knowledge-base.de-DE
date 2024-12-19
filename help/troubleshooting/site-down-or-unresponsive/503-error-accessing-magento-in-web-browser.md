---
title: 503-Fehler beim Zugriff auf Adobe Commerce im Webbrowser
description: Dieser Artikel bietet eine mögliche Lösung für das Problem, dass beim Versuch, auf die Adobe Commerce-Storefront und/oder Admin zuzugreifen, der Fehler „503“ auftritt.
exl-id: 4232aa21-40c2-41b0-9fb0-fc8cd4db8e39
feature: Storefront
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# 503-Fehler beim Zugriff auf Adobe Commerce im Webbrowser

Dieser Artikel bietet eine mögliche Lösung für das Problem, dass beim Versuch, auf die Adobe Commerce-Storefront und/oder Admin zuzugreifen, der Fehler „503“ auftritt.

## Betroffene Produkte und Versionen

Adobe Commerce 2.3.x

## Problem {#symptoms}

<u>Schritte zur Reproduktion</u>

(Voraussetzungen: Stellen Sie sicher, dass sich der Speicher nicht im [Wartungsmodus](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/set-mode#config-mode-show) befindet.

Navigieren Sie in einem Webbrowser zu Ihrer Commerce Admin oder Storefront.

<u>Erwartetes Ergebnis</u>

Die Seite wird geladen.

<u>Tatsächliches Ergebnis</u>

Der HTTP-Fehler 503 (Dienst nicht verfügbar) wird angezeigt. Der Apache-`error.log` enthält die folgende Meldung:

*Ungültiger Befehl „order“, möglicherweise falsch geschrieben oder von einem Modul definiert, das nicht in der Server-Konfiguration enthalten ist.*

## Ursache {#details}

Das Apache 2.4-Kompatibilitätsmodul `mod_access_compat` ist deaktiviert, was dazu führt, dass Adobe Commerce-URL-Neuschreibungen nicht ordnungsgemäß funktionieren.

## Lösung {#suggested-solution}

Aktivieren Sie das `mod_access_compat` Apache-Modul und starten Sie Apache neu, indem Sie Folgendes als Benutzer mit „Root“-Berechtigungen ausführen:

```bash
a2enmod access_compat
service <name> restart
```

Unter CentOS

```bash
<name>
```

ist

```bash
httpd
```

. Auf Ubuntu,

```bash
<name>
```

ist

```bash
apache2
```

.

## Verwandtes Lesen {#additional-resources}

* [Apache-Dokumentation zu mod\_access\_compat](https://httpd.apache.org/docs/current/mod/mod_access_compat.html)
* [Apache-Dokumentation zu mod\_authz\_host](https://httpd.apache.org/docs/current/mod/mod_authz_host.html)
* [Reihenfolge, Zulassen, Ablehnen über das Apache-Handbuch](https://docstore.mik.ua/orelly/linux/apache/ch05_06.htm)
* [askubuntu.com](https://askubuntu.com/questions/335228/changes-in-apache-config-between-12-04-2-and-12-04-3-lts)
