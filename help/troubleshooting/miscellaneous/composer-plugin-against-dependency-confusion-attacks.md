---
title: Composer-Plug-in gegen Abhängigkeitskonfusionsangriffe
description: Dieser Artikel enthält Informationen zum Composer-Plug-in, das für die Abhängigkeitskonfusionsangriffe veröffentlicht wurde, und Empfehlungen zur Vermeidung des Fehlers. Das Composer-Plug-in wurde mit Adobe Commerce-Version 2.4.3 eingeführt, um Adobe Commerce-Händler vor Abhängigkeitskonfusionsangriffen zu schützen.
exl-id: 42543043-cf60-4431-80e9-866771c5c87b
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# Composer-Plug-in gegen Abhängigkeitskonfusionsangriffe

Dieser Artikel enthält Informationen zum Composer-Plug-in, das für die Abhängigkeitskonfusionsangriffe veröffentlicht wurde, und Empfehlungen zur Vermeidung des Fehlers. Das Composer-Plug-in wurde mit Adobe Commerce-Version 2.4.3 eingeführt, um Adobe Commerce-Händler vor Abhängigkeitskonfusionsangriffen zu schützen.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.3 und zukünftige Versionen (alle Bereitstellungsmethoden)

## Problem

Ein potenzieller Fall eines aktiven Abhängigkeitskonflikts wird durch mindestens eine der in `composer.json` vom Composer-Plug-in `magento/composer-dependency-version-audit-plugin` während der Installation/Aktualisierung des Composers.

<u>Zu reproduzierende Schritte</u>:

Wenn Sie Composer installieren/aktualisieren, stoppt das Composer-Plug-in den Prozess, wenn es einen möglichen Abhängigkeitskonflikt erkennt. In diesem Fall schlägt die Installation/Aktualisierung des Composers mit einer Fehlermeldung ähnlich der folgenden fehl:

*```Higher matching version x.x.x of package/name was found in public repository packagist.org than x.x.x in private.repo. Public package might've been taken over by a malicious entity; please investigate and update package requirement to match the version from the private repository.```*

## Ursache

Abhängigkeitskonfusion-Angriff ermöglicht es, beliebigen Code auf einem Server remote auszuführen, indem ein Abhängigkeitsmanager (z. B. der PHP-Composer) dazu gebracht wird, ein bösartiges Paket aus einer öffentlichen Quelle anstatt aus dem ursprünglichen Paket aus einem privaten Repository herunterzuladen.

Ein solcher Angriff kann sogar unentdeckt bleiben, wenn ein Angreifer die Funktionalität des Originalpakets beibehalten kann.

Angreifer können diese Verwundbarkeit ausnutzen, wenn ein Paket nur über private Repositorys verfügbar ist, aber nicht im öffentlichen Verzeichnis registriert ist. Der Angreifer lädt dann ein Paket mit demselben Namen in das öffentliche Repository hoch und gibt ihm eine höhere Version als die privat verfügbare. Der Abhängigkeitsmanager vergleicht dann Versionen von sowohl privaten als auch öffentlich verfügbaren Paketen und wählt das höchste aus dem öffentlichen Repository aus. Der vom Abhängigkeitsmanager heruntergeladene böswillige Code wird dann mit denselben Berechtigungen wie der Code der Anwendung ausgeführt.

## Lösung

### Recommendations für Händler

* Nehmen Sie die Fehlermeldung auf, die angezeigt wird, wenn das Plug-in die Installation/Aktualisierung des Composers stoppt, und wenden Sie sich an den Entwickler der Erweiterung, wenn Sie das potenziell kompromittierte Paket erkennen.
* Sie können Adobe Commerce weiterhin mit der sicheren Paketversion vom Marketplace oder einem anderen vertrauenswürdigen privaten Repository installieren.
* Ändern Sie die erforderliche Paketversion in Ihrer Composer.json in die exakte Version, die im Marketplace gefunden wurde, um mit der Installation/Aktualisierung des Composers fortzufahren.

### Erwartungen von Erweiterungsentwicklern

* Es gibt keine Möglichkeit zu wissen, ob das Paket für ein Plugin, wenn von einem öffentlichen Repo, kompromittiert wurde oder nicht. Das Plug-in erkennt, wenn eine öffentliche Version eines Pakets unter packagist.org eine höhere Version aufweist als die Version, die von einem privaten Repo wie [repo.magento.com](https://repo.magento.com). Wir empfehlen dringend, dass Erweiterungsentwickler solche Situationen vermeiden und keine neueren Versionen veröffentlichen, als über verfügbar sind [repo.magento.com](https://repo.magento.com).
* Adobe Commerce weiß, dass der Marketplace-Überprüfungsprozess die Verfügbarkeit von Erweiterungen verzögern kann. Der Prozess ist jedoch erforderlich, um Händler sicher zu halten und Entwicklern von Erweiterungen zu helfen, versehentliche Fehler zu finden, die sie möglicherweise verpasst haben.
