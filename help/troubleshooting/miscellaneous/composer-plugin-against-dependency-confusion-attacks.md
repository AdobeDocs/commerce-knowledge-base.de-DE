---
title: Composer-Plug-in gegen Dependency Confusion-Angriffe
description: Dieser Artikel enthält Informationen zum Composer-Plug-in, das für die Dependency Confusion-Angriffe veröffentlicht wurde, und Empfehlungen zur Vermeidung des Fehlers. Das Composer-Plug-in wurde zusammen mit der Adobe Commerce-Version 2.4.3 eingeführt, um Adobe Commerce-Händler vor Abhängigkeiten-Verwirrung-Angriffen zu schützen.
exl-id: 42543043-cf60-4431-80e9-866771c5c87b
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# Composer-Plug-in gegen Dependency Confusion-Angriffe

Dieser Artikel enthält Informationen zum Composer-Plug-in, das für die Dependency Confusion-Angriffe veröffentlicht wurde, und Empfehlungen zur Vermeidung des Fehlers. Das Composer-Plug-in wurde zusammen mit der Adobe Commerce-Version 2.4.3 eingeführt, um Adobe Commerce-Händler vor Abhängigkeiten-Verwirrung-Angriffen zu schützen.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.3 und zukünftige Versionen (alle Bereitstellungsmethoden)

## Problem

Ein potenzieller Fall eines aktiven Abhängigkeitsverwechslungsangriffs wird durch mindestens eine der direkten oder indirekten Abhängigkeiten erkannt, die in `composer.json` vom Composer-Plug-in `magento/composer-dependency-version-audit-plugin` während der Installation/Aktualisierung des Composers definiert wurden.

<u>Schritte zur Reproduktion</u>:

Wenn Sie Composer installieren/aktualisieren, stoppt das Composer-Plug-in den Prozess, wenn es einen potenziellen Angriff auf Dependency Confusion entdeckt. In diesem Fall schlägt die Installation/Aktualisierung von Composer mit einer Fehlermeldung ähnlich der folgenden fehl:

*```Higher matching version x.x.x of package/name was found in public repository packagist.org than x.x.x in private.repo. Public package might've been taken over by a malicious entity; please investigate and update package requirement to match the version from the private repository.```*

## Ursache

Dependency Confusion ermöglicht es, beliebigen Code aus der Ferne auf einem Server auszuführen, indem ein Dependency Manager (z.B. PHP&#39;s Composer) dazu gebracht wird, ein bösartiges Paket aus einer öffentlichen Quelle herunterzuladen, anstatt das ursprüngliche Paket aus einem privaten Repository.

Ein solcher Angriff kann sogar unentdeckt bleiben, wenn ein Angreifer in der Lage ist, die Funktionalität des ursprünglichen Pakets beizubehalten.

Angreifer können diese Sicherheitslücke ausnutzen, wenn ein Paket nur über private Repositorys verfügbar ist, aber nicht im öffentlichen registriert ist. Der Angreifer lädt dann ein Paket mit demselben Namen in das öffentliche Repository hoch und gibt ihm eine höhere Version als die privat verfügbare. Der Abhängigkeits-Manager vergleicht dann Versionen von sowohl privaten als auch öffentlich verfügbaren Paketen und wählt die höchste aus dem öffentlichen Repository aus. Der vom Abhängigkeits-Manager heruntergeladene bösartige Code wird dann mit denselben Berechtigungen wie der Code der Anwendung ausgeführt.

## Lösung

### Recommendations an Händler

* Nehmen Sie die Fehlermeldung, die angezeigt wird, wenn das Plug-in die Composer-Installation/-Aktualisierung stoppt, ernst, und wenden Sie sich an den Entwickler der Erweiterung, wenn Sie das potenziell kompromittierte Paket erkennen.
* Sie können Adobe Commerce weiterhin mit der sicheren Paketversion vom Marketplace oder einem anderen vertrauenswürdigen privaten Repository installieren.
* Ändern Sie die erforderliche Paketversion in Ihrer composer.json in die exakte Version auf dem Marketplace, um mit der Installation/Aktualisierung des Composers fortzufahren.

### Erwartungen der Erweiterungsentwickler

* Es gibt keine Möglichkeit, mit Sicherheit festzustellen, ob das Paket für ein Plug-in, von einem öffentlichen Repository, kompromittiert wurde oder nicht. Das Plug-in erkennt, wenn eine öffentliche Version eines Pakets unter packagist.org eine höhere Version als die von einem privaten Repository wie [repo.magento.com) ](https://repo.magento.com). Es wird dringend empfohlen, dass Erweiterungsentwickler solche Situationen vermeiden und keine neueren Versionen veröffentlichen, als die über [repo.magento.com](https://repo.magento.com) verfügbaren.
* Adobe Commerce weiß, dass der Marketplace-Überprüfungsprozess die Verfügbarkeit von Erweiterungen verzögern kann, aber der Prozess ist dazu da, Händler zu schützen und Entwicklern von Erweiterungen dabei zu helfen, versehentliche Fehler zu finden, die sie möglicherweise übersehen haben.
