---
title: Bereitstellungsfehler bei der Aktivierung des Frühalphanumermoduls
description: Beim Einsatz des Baler-Moduls in einer Produktionsumgebung treten beim Händler Bereitstellungsfehler auf, da sich die Funktion derzeit in der frühen Phase der Alpha-Entwicklung befindet.
exl-id: 6cdac0a5-eaeb-467d-8369-9017aed6219e
feature: Build, Deploy, Extensions, SCD, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# Bereitstellungsfehler bei der Aktivierung des Frühalphanumermoduls

Beim Einsatz des Baler-Moduls in einer Produktionsumgebung treten beim Händler Bereitstellungsfehler auf, da sich die Funktion derzeit in der frühen Phase der Alpha-Entwicklung befindet.

>[!WARNING]
>
>Das frühe Alpha-Baler-JavaScript-Bundling ist noch nicht einsatzbereit und wird auf eigene Gefahr verwendet.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.3.x und 2.4.x.
* Adobe Commerce vor Ort 2.3.x und 2.4.x.

## Problem

Wir empfehlen Händlern nicht, das Baler-Modul in einer Produktionsumgebung zu verwenden, da es sich derzeit in der frühen Alpha-Entwicklungsphase befindet. Die Verwendung dieser Funktion kann zu Implementierungsfehlern führen.

<u>Zu reproduzierende Schritte</u>:

1. Der Händler versucht, die Variable **SCD\_USE\_BALER** in die Build-Phase der Datei `.magento.env.yaml` einzufügen, wodurch das Baler-JavaScript-Bundle-Paket aktiviert wird.
1. Der Händler fügt außerdem die Abhängigkeit des Baler Composer hinzu: `"magento/module-baler": "1.0.0-alpha"` zum Abschnitt `require` von `composer.json`.

<u>Erwartetes Ergebnis</u>:

Erfolgreiche Implementierung.

<u>Tatsächliches Ergebnis</u>:

Der Händler sieht in den Bereitstellungsprotokollen in der Cloud die folgende Fehlermeldung: `<project home>/var/log/cloud.log` bei der Bereitstellung statischer Inhalte:

```
[2020-08-19 12:06:12] WARNING: [1007] Baler JS bundling cannot be used because of the following issues:
        [2020-08-19 12:06:12] WARNING:  - Path to baler executable could not be found. The Node package may not be installed or may not be linked.
```

## Ursache

Das Baler-Modul befindet sich derzeit in der Anfangsphase der Alpha-Entwicklung und der Installationsprozess der Baler-Erweiterung ist komplex.

## Lösung

Sie können die vorhandene Baler-Alpha-Dokumentation unter [Github/Magento/Baler/Erste Schritte mit dem Alpha](https://github.com/magento/baler/blob/master/docs/ALPHA.md) lesen. Es ist jedoch nicht einsatzbereit und wird auf eigene Gefahr verwendet. Stattdessen wird empfohlen, JavaScript-Dateien (JS) mithilfe des integrierten Adobe Commerce-Bundles (Basis-Bundling) zur Dateioptimierung zusammenzuführen oder zu bündeln.

* Sie können das Zusammenführen oder Bundling im Admin aktivieren (das Zusammenführen und Bundling kann nicht gleichzeitig aktiviert werden): **Stores** > **Einstellungen** > **Konfiguration** > **Erweitert** > **Entwickler** > **JavaScript-Einstellungen**.
* Sie können auch das integrierte Bundling (Basis-Bundling) von Adobe Commerce über die Befehlszeile aktivieren: `php -f bin/magento config:set dev/js/enable_js_bundling 1`

Weitere Informationen finden Sie unter [CSS- und JavaScript-Dateioptimierung in Adobe Commerce für Cloud-Infrastruktur und Adobe Commerce On-Premise](https://support.magento.com/hc/en-us/articles/360044482152).
