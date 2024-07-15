---
title: Geringe Site- und API-Leistung
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce-Problem in der Cloud-Infrastruktur 2.2.1 in Zusammenhang mit einer niedrigen Site- und API-Leistung, die durch eine lange Zeit verursacht wird, die zum Schreiben von "debug.log"erforderlich ist.
exl-id: b71816cd-f580-4c80-9694-585ed051a56d
feature: REST, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Geringe Site- und API-Leistung

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce-Problem in der Cloud-Infrastruktur 2.2.1 in Zusammenhang mit einer niedrigen Site- und API-Leistung, die durch eine lange zum Schreiben von `debug.log` erforderliche Zeit verursacht wird.

## Problem

Die Site-Leistung ist langsam. API-Vorgänge werden langsam ausgeführt, z. B. beim Aktualisieren von Produkten mit der `PUT` -Methode. Wenn Sie sich die Vorgänge mit New Relic genauer ansehen, werden die meisten Arbeitsspeicher und CPU durch Schreiben in `/var/log/debug.log` belegt.

## Lösung

Um das Problem zu lösen, wenden Sie den Patch an. Der Patch teilt und schreibt die Logs für Protokoll-, Zahlungs- und Versandmethoden in separate Dateien.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-8371\_EE\_2.2.1\_COMPOSER\_v2.patch herunterladen](assets/MDVA-8371_EE_2.2.1_COMPOSER_v2.patch.zip)

### Kompatible Adobe Commerce-Versionen

Der Patch wurde für erstellt:

* Adobe Commerce in Cloud-Infrastruktur 2.2.1

Der Patch ist auch mit den folgenden Adobe-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce auf Cloud-Infrastruktur 2.2.0, 2.2.2, 2.2.3
* Adobe Commerce vor Ort 2.2.0, 2.2.2, 2.2.3

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches in unserer Support-Wissensdatenbank.

## Attached Files
