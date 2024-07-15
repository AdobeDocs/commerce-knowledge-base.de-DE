---
title: Langsame Leistung, langsame und lange laufende Crons
description: In diesem Artikel wird beschrieben, wie Sie Probleme mit der Site-Leistung und langsame laufende und hängende Crons lösen können, die durch flache Tabellen und Indexer verursacht werden, die aktiviert wurden.
exl-id: a78ca3c3-85b4-40a1-a693-4703dd3ef4b5
feature: Best Practices, Cache, Categories, Catalog Management
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Langsame Leistung, langsame und lange laufende Crons

>[!WARNING]
>
>Da einige Erweiterungen nur mit flachen Tabellen funktionieren, besteht bei allen Adobe Commerce-Versionen die Gefahr, dass flache Tabellen deaktiviert werden. Wenn Sie wissen, dass Sie über einige Erweiterungen verfügen, die Indexer für flache Kataloge verwenden, müssen Sie dies bei der Festlegung dieser Werte auf &quot;*Nein* &quot;berücksichtigen.

In diesem Artikel wird beschrieben, wie Sie Probleme mit der Site-Leistung und langsame laufende und hängende Crons lösen können, die durch die Aktivierung von [flachen Tabellen und Indexern](https://docs.magento.com/m2/ce/user_guide/catalog/catalog-flat.html) verursacht wurden.

BETROFFENE PRODUKTE UND VERSIONEN

* Adobe Commerce auf Cloud-Infrastruktur 2.1.x und höher
* Adobe Commerce On-Premise 2.1.x und höher
* Magento Open Source 2.1.x und höher

## Problem

Einfache Indexe können Folgendes verursachen:

* Schwerwiegende Probleme mit SQL-Load und Site-Performance.
* Lange Laufkronen und klebte.

## Ursache

Einfache Tabellen und Indexer aktiviert.

## Lösung {#solution}

Ab Adobe Commerce und Magento Open Source 2.1.x und höher ist die Verwendung eines reduzierten Katalogs keine Best Practice mehr und wird nicht empfohlen. Die kontinuierliche Verwendung dieser Funktion führt bekanntermaßen zu Leistungsbeeinträchtigungen und anderen Indizierungsproblemen. So deaktivieren Sie den flachen Katalog:

1. Navigieren Sie im Admin zu &quot;**Stores**&quot;> &quot;**Einstellungen**&quot;> &quot;**Konfiguration**&quot;.
1. Wählen Sie im Bereich auf der linken Seite unter **Katalog** die Option **Katalog**.
1. Erweitern Sie den Abschnitt **Storefront** und gehen Sie wie folgt vor:
   * Setzen Sie **Kategorie des flachen Katalogs verwenden** auf *NEIN*.
   * Setzen Sie **Flachkatalog-Produkt verwenden** auf *Nein*.
1. Klicken Sie nach Abschluss des Vorgangs auf **Konfiguration speichern**. Aktualisieren Sie dann den Cache, wenn Sie dazu aufgefordert werden.
1. Leeren Sie den Cache, indem Sie `php bin/magento cache:flush` ausführen.

Wenn Sie die Kategorie **Flachen Katalog verwenden** und die Kategorie **Flachkatalog-Produkt verwenden** nicht in *Nein* ändern können, da die Optionen ausgegraut sind, deaktivieren Sie flache Indexer in `app/etc/config.php`:

1. Führen Sie diesen Befehl aus, um sicherzustellen, dass alle Indexer nach Zeitplan auf Aktualisieren eingestellt sind: `php bin/magento indexer:set-mode schedule`.
1. Bearbeiten Sie `app/etc/config.php` und suchen Sie die Zeilen mit `flat_catalog_product` und `flat_catalog_category` - ändern Sie sie von 1 in 0, um sie zu deaktivieren.
1. Führen Sie den Befehl `php bin/magento app:config:import` aus.
1. Führen Sie diesen Befehl aus, um sicherzustellen, dass die flachen Indexer deaktiviert sind: `php        bin/magento indexer:status`.
1. Leeren Sie den Cache, indem Sie `php bin/magento cache:flush` ausführen.

## Verwandte Informationen

[Setzen Sie hängengebliebene Adobe Commerce-Cron-Aufträge manuell auf Cloud](/help/how-to/general/reset-stuck-magento-cron-jobs-manually-on-cloud.md) in unserer Support-Wissensdatenbank zurück.
