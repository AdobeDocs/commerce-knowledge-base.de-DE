---
title: Google Analytics verfolgt keine Konversionsdaten
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.2.4-Problem in Bezug auf Google Analytics, die die Konversionsdaten nicht verfolgen.
exl-id: b9012fd1-4f90-41e9-9559-0343ee052ec6
feature: Configuration, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Google Analytics verfolgt keine Konversionsdaten

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.2.4-Problem in Bezug auf Google Analytics, die die Konversionsdaten nicht verfolgen.

>[!NOTE]
>
>Das Problem wurde in Adobe Commerce 2.2.6 behoben.

## Problem

Die Konversionsdaten wurden von Google Analytics aufgrund eines Fehlers im Komponentencode der Google Analytics nicht verfolgt.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren und konfigurieren Sie die Google Analytics-Funktion in Commerce Admin unter **Stores** > **Einstellungen** > **Konfiguration** > **Vertrieb** > **Google-API** > **Google Analytics**.
1. Klicks **Konfiguration speichern**.
1. Positionieren Sie eine Bestellung auf der Storefront.
1. Navigieren Sie zu **Google Analytics-Dashboard** > **Konversionen** > **Übersicht**.
1. Stellen Sie den Datumsbereich auf das aktuelle Datum ein.

<u>Erwartetes Ergebnis</u>:

Die Reihenfolge wird in den Konversionsdaten angezeigt.

<u>Tatsächliches Ergebnis</u>:

Die Reihenfolge wird nicht in den Konversionsdaten angezeigt.

## Lösung

Der Patch behebt den Fehler im Komponentencode der Google Analytics. Nach dem Anwenden der Patch-Konvertierungsdaten werden von Google Analytics nachverfolgt.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-11263\_EE\_2.2.4\_v1.composer.patch herunterladen](assets/MDVA-11263_EE_2.2.4_v1.composer.patch.zip)

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce vor Ort 2.2.4

Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce vor Ort 2.2.5
* Adobe Commerce in Cloud-Infrastruktur 2.2.4, 2.2.5

## Anwenden des Pflasters

Siehe [Anwenden eines von Adobe Commerce bereitgestellten Komponentenpatches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) für Anweisungen.

## Attached Files
