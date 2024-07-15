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

<u>Voraussetzungen</u>: Erstellen Sie eine Bestellung mithilfe der Versandmethode FedEx, DHL, UPS oder USPS.

### Szenario 1: Beim Hinzufügen einer Sendung einen Titel erstellen

<u>Zu reproduzierende Schritte:</u>

1. Öffnen Sie die platzierte Bestellung im Admin unter **Verkauf** > **Bestellungen**.
1. Klicken Sie auf die Schaltfläche **Schiff** . Die Seite **Neue Sendung** wird geöffnet.

<u>Erwartetes Ergebnis:</u>

Das Kontrollkästchen **Versandtitel erstellen** wird unten auf der Seite angezeigt.

<u>Tatsächliches Ergebnis:</u>

Das Kontrollkästchen **Versandtitel erstellen** wird nicht angezeigt.

### Szenario 2: Erstellen eines Etiketts für eine bestehende Sendung

<u>Zu reproduzierende Schritte:</u>

1. Öffnen Sie die platzierte Bestellung im Admin unter **Verkauf** > **Bestellungen**.
1. Klicken Sie auf die Schaltfläche **Schiff** . Die Seite **Neue Sendung** wird geöffnet.
1. Klicken Sie auf die Schaltfläche **Sendung senden** . Eine Sendung wird erstellt.
1. Öffnen Sie die neu erstellte Sendung.
1. Klicken Sie auf die Schaltfläche **Versandtitel erstellen** . Das Dialogfeld **Pakete erstellen** wird geöffnet.

<u>Erwartetes Ergebnis:</u>

Die Schaltfläche **Produkte zum Paket hinzufügen** im modalen Fenster **Pakete erstellen** zeigt Felder mit Bestellelementen an.

<u>Tatsächliches Ergebnis:</u>

Das modale Fenster **Pakete erstellen** wird nicht ordnungsgemäß angezeigt. Es ist nicht möglich, der Sendung Bestellelemente hinzuzufügen.

## Lösung

Wenden Sie den in diesem Artikel bereitgestellten Patch an.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MC-35514-2.4.0-CE-Composer-2.patch](assets/MC-35514-2.4.0-CE-composer-2.patch.zip)

Der Patch kann auch in den Formaten `.git` und `.composer` heruntergeladen werden, und zwar auf der Seite [Adobe Commerce-Downloads](https://magento.com/tech-resources/download) unter **Patches** in der linken Spaltennavigation. Suchen Sie nach dem Patch MC-35514 .

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce auf Cloud-Infrastruktur, Version 2.4.0
* Adobe Commerce On-Premise Version 2.4.0

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches.

## Attached Files
