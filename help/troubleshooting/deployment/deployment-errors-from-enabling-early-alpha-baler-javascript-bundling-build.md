---
title: Bereitstellungsfehler durch Aktivierung des Alpha-Ballenpressenmoduls
description: Bei der Verwendung des Ballenmoduls in einer Produktionsumgebung treten Bereitstellungsfehler auf, da sich die Funktion derzeit in der frühen Alpha-Entwicklungsphase befindet.
exl-id: 6cdac0a5-eaeb-467d-8369-9017aed6219e
feature: Build, Deploy, Extensions, SCD, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# Bereitstellungsfehler durch Aktivierung des Alpha-Ballenpressenmoduls

Bei der Verwendung des Ballenmoduls in einer Produktionsumgebung treten Bereitstellungsfehler auf, da sich die Funktion derzeit in der frühen Alpha-Entwicklungsphase befindet.

>[!WARNING]
>
>Das Early-Alpha Baller JavaScript Bundling ist nicht produktionsbereit und wird auf eigenes Risiko verwendet.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastrukturen 2.3.x und 2.4.x.
* Adobe Commerce On-Premises 2.3.x und 2.4.x.

## Problem

Wir raten davon ab, dass Händler das Modul Ballenpresse in einer Produktionsumgebung verwenden, da es sich derzeit in der frühen Alpha-Entwicklungsphase befindet. Die Verwendung kann zu Bereitstellungsfehlern führen.

<u>Schritte zur Reproduktion</u>:

1. Der Händler versucht, die Variable **SCD\_USE\_BALER** in der Build-Phase der `.magento.env.yaml`-Datei einzufügen, wodurch das Baler-JavaScript-Bundling-Paket aktiviert wird.
1. Der Händler fügt auch die Abhängigkeit Ballenpressen-Komponist hinzu: `"magento/module-baler": "1.0.0-alpha"` zu `require` Abschnitt der `composer.json`.

<u>Erwartetes Ergebnis</u>:

Erfolgreiche Bereitstellung.

<u>Tatsächliches </u>:

Der Händler sieht die folgende Fehlermeldung in den Bereitstellungsprotokollen in der Cloud, die beim Bereitstellungsschritt des statischen Inhalts `<project home>/var/log/cloud.log` wird:

```
[2020-08-19 12:06:12] WARNING: [1007] Baler JS bundling cannot be used because of the following issues:
        [2020-08-19 12:06:12] WARNING:  - Path to baler executable could not be found. The Node package may not be installed or may not be linked.
```

## Ursache

Das Modul Ballenpresse befindet sich derzeit in der frühen Alpha-Entwicklungsphase, und der Installationsprozess der Ballenpresse-Erweiterung ist komplex.

## Lösung

Die aktuelle Dokumentation zum Baler Alpha finden Sie unter [Github/Magento/Baler/Getting Started with the alpha](https://github.com/magento/baler/blob/master/docs/ALPHA.md). Es ist jedoch nicht für die Verwendung in der Produktion bereit und wird auf eigenes Risiko verwendet. Es wird stattdessen empfohlen, JavaScript (JS)-Dateien mithilfe des integrierten Bundles (Basic Bundling) von Adobe Commerce zusammenzuführen oder zu bündeln, um die Datei zu optimieren.

* Sie können die Zusammenführung oder Bündelung im Admin aktivieren (Zusammenführung und Bündelung können nicht gleichzeitig aktiviert werden): **Stores** > **Settings** > **Configuration** > **Advanced** > **Developer** > **JavaScript Settings**.
* Sie können auch die integrierte Bündelung von Adobe Commerce (einfache Bündelung) über die Befehlszeile aktivieren: `php -f bin/magento config:set dev/js/enable_js_bundling 1`

Weitere Informationen finden Sie unter [CSS- und JavaScript-Dateioptimierung auf Adobe Commerce in Cloud-Infrastrukturen und Adobe Commerce On-Premise](https://support.magento.com/hc/en-us/articles/360044482152).
