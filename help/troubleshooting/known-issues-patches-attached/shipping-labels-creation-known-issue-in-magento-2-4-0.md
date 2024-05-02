---
title: Bekanntes Problem bei der Erstellung von Versandbeschriftungen in Adobe Commerce 2.4.0
description: Dieser Artikel enthält einen Patch für ein bekanntes Adobe Commerce 2.4.0-Problem, bei dem keine Versandbeschriftung erstellt werden kann.
exl-id: 722689d9-0c90-4a9d-8449-e93c6585b7c3
feature: Orders, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Bekanntes Problem bei der Erstellung von Versandbeschriftungen in Adobe Commerce 2.4.0

Dieser Artikel enthält einen Patch für ein bekanntes Adobe Commerce 2.4.0-Problem, bei dem keine Versandbeschriftung erstellt werden kann.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.4.0
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

## Problem

<u>Voraussetzungen</u>: Erstellen Sie eine Bestellung mit der Versandmethode FedEx, DHL, UPS oder USPS.

### Szenario 1: Beim Hinzufügen einer Sendung einen Titel erstellen

<u>Zu reproduzierende Schritte:</u>

1. Öffnen Sie die platzierte Bestellung unter &quot;Admin&quot;. **Vertrieb** > **Bestellungen**.
1. Klicken Sie auf **Schiff** Schaltfläche. Die **Neue Sendungen** Seite geöffnet.

<u>Erwartetes Ergebnis:</u>

Die **Versandtitel erstellen** wird unten auf der Seite angezeigt.

<u>Ergebnis:</u>

Die **Versandtitel erstellen** nicht angezeigt.

### Szenario 2: Erstellen eines Etiketts für eine bestehende Sendung

<u>Zu reproduzierende Schritte:</u>

1. Öffnen Sie die platzierte Bestellung unter &quot;Admin&quot;. **Vertrieb** > **Bestellungen**.
1. Klicken Sie auf **Schiff** Schaltfläche. Die **Neue Sendungen** Seite geöffnet.
1. Klicken Sie auf **Sendung übermitteln** Schaltfläche. Eine Sendung wird erstellt.
1. Öffnen Sie die neu erstellte Sendung.
1. Klicken Sie auf **Versandtitel erstellen** Schaltfläche. Die **Erstellen von Paketen** wird geöffnet.

<u>Erwartetes Ergebnis:</u>

Die **Produkte zum Paket hinzufügen** Schaltfläche auf der **Erstellen von Paketen** modales Fenster zeigt Felder mit Bestellelementen an.

<u>Ergebnis:</u>

Die **Erstellen von Paketen** modales Fenster nicht richtig angezeigt wird, ist es nicht möglich, Bestellartikel zur Sendung hinzuzufügen.

## Lösung

Wenden Sie den in diesem Artikel bereitgestellten Patch an.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MC-35514-2.4.0-CE-Composer-2.patch](assets/MC-35514-2.4.0-CE-composer-2.patch.zip)

Der Patch kann auch in beiden heruntergeladen werden. `.git` und `.composer`, Formate in [Adobe Commerce-Downloads](https://magento.com/tech-resources/download) Seite, unter **Patches** in der linken Spaltennavigation. Suchen Sie nach dem Patch MC-35514 .

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce auf Cloud-Infrastruktur, Version 2.4.0
* Adobe Commerce On-Premise Version 2.4.0

## Anwenden des Pflasters

Siehe [Anwenden eines von Adobe bereitgestellten Composer-Patches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) für Anweisungen.

## Attached Files
