---
title: Langsame Leistung, langsame und lange laufende Crons
description: In diesem Artikel wird beschrieben, wie Sie Probleme mit der Site-Leistung sowie langsame und steckengebliebene Krone beheben können, die durch flache Tabellen und Indexer verursacht wurden, die aktiviert wurden.
exl-id: a78ca3c3-85b4-40a1-a693-4703dd3ef4b5
feature: Best Practices, Cache, Categories, Catalog Management
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Langsame Leistung, langsame und lange laufende Crons

>[!WARNING]
>
>Da einige Erweiterungen nur mit flachen Tabellen funktionieren, besteht bei jeder Adobe Commerce-Version das Risiko, dass Sie flache Tabellen deaktivieren. Wenn Sie wissen, dass Sie einige Erweiterungen haben, die Indexer für flache Kataloge verwenden, müssen Sie dies möglicherweise berücksichtigen, wenn Sie diese Werte auf &quot;*&quot;*.

In diesem Artikel wird beschrieben, wie Sie Probleme mit der Site-Leistung beheben und langsame und steckengebliebene Crons [, die durch die Aktivierung ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/catalog-flat)flachen Tabellen und Indexern“ verursacht wurden.

BETROFFENE PRODUKTE UND VERSIONEN

* Adobe Commerce auf Cloud-Infrastruktur 2.1.x und höher
* Adobe Commerce On-Premises 2.1.x und höher
* Magento Open Source 2.1.x und höher

## Problem

Flache Indexer können Folgendes verursachen:

* Starke SQL-Last und Probleme mit der Site-Performance.
* Lang laufende und stecken gebliebene Crons.

## Ursache

Flache Tabellen und Indexer aktiviert.

## Lösung {#solution}

Ab Adobe Commerce und Magento Open Source 2.1.x und höher ist die Verwendung eines einfachen Katalogs keine Best Practice mehr und wird nicht empfohlen. Es ist bekannt, dass die kontinuierliche Verwendung dieser Funktion zu Leistungseinbußen und anderen Indizierungsproblemen führt. So deaktivieren Sie den flachen Katalog:

1. Navigieren Sie in Admin zu **Stores** > **Einstellungen** > **Konfiguration**.
1. Wählen Sie im Bedienfeld links unter **Katalog** die Option **Katalog** aus.
1. Erweitern Sie den **Storefront**-Abschnitt und führen Sie folgende Schritte aus:
   * Legen Sie **Flache Katalogkategorie verwenden** auf *Nein* fest.
   * Legen **Flaches Katalogprodukt verwenden** auf &quot;*&quot;*.
1. Klicken Sie abschließend auf **Konfiguration speichern**. Aktualisieren Sie dann bei Aufforderung den Cache.
1. Cache durch Ausführen von `php bin/magento cache:flush` leeren.

Wenn Sie die Optionen **Geglättete Katalogkategorie verwenden** und **Geglättetes Katalogprodukt verwenden** nicht in *Nein* ändern können, da die Optionen ausgegraut sind, deaktivieren Sie in `app/etc/config.php`:

1. Führen Sie diesen Befehl aus, um sicherzustellen, dass alle Indexer auf „Nach Zeitplan aktualisieren“ eingestellt sind: `php bin/magento indexer:set-mode schedule`.
1. Bearbeiten Sie `app/etc/config.php` und suchen Sie die Zeilen mit `flat_catalog_product` und `flat_catalog_category` - ändern Sie sie von 1 auf 0, um sie zu deaktivieren.
1. Ausführen des `php bin/magento app:config:import`
1. Führen Sie diesen Befehl aus, um zu bestätigen, dass die flachen Indexer deaktiviert sind: `php        bin/magento indexer:status`.
1. Cache durch Ausführen von `php bin/magento cache:flush` leeren.

## Ergänzende Informationen

[Setzen Sie Adobe Commerce Cron-Aufträge manuell in der Cloud zurück](/help/how-to/general/reset-stuck-magento-cron-jobs-manually-on-cloud.md) in unserer Support-Wissensdatenbank.
