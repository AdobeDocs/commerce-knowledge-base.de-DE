---
title: '"Adobe Commerce 2.4.0 B2B: falsche Bestelllogik bei abgelaufenem Rabatt'
description: Dieser Artikel enthält einen Patch für die bekannte Ausgabe eines Bestellrabatts (Bestellwert), der in Adobe Commerce 2.4.0 B2B nicht angewendet wird. Wenn die Bestellung mit einem Rabattcode versehen wurde, der abgelaufen ist, während sich die Bestellung im Genehmigungsprozess befand, spiegelt die genehmigte Bestellung den Rabatt nicht wider.
exl-id: 3ef41655-c31e-4e9c-8985-fa1b4fd53170
feature: B2B, Orders, Payments, Personalization, Purchase Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 B2B: falsche Bestelllogik bei abgelaufenem Rabatt

Dieser Artikel enthält einen Patch für die bekannte Ausgabe eines Bestellrabatts (Bestellwert), der in Adobe Commerce 2.4.0 B2B nicht angewendet wird. Wenn die Bestellung mit einem Rabattcode versehen wurde, der abgelaufen ist, während sich die Bestellung im Genehmigungsprozess befand, spiegelt die genehmigte Bestellung den Rabatt nicht wider.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.4.0
* Adobe Commerce vor Ort 2.4.0

## Problem

<u>Voraussetzungen</u>: Es wird ein Rabattgutschein erstellt, und es gibt Genehmigungsregeln, die verhindern, dass POs automatisch verarbeitet werden.

<u>Zu reproduzierende Schritte:</u>

1. Platzieren Sie eine Bestellung mit angewendetem Rabatt.
1. Deaktivieren Sie den Rabattgutschein.
1. Genehmigen Sie die Bestellung als Geschäftsführer.
1. Überprüfen Sie die resultierende Bestellung.

<u>Erwartetes Ergebnis:</u>

Die Bestellung wird mit einem ermäßigten Gesamtwert erstellt.

<u>Tatsächliches Ergebnis:</u>

Die Bestellung wird für den vollen Betrag erstellt.

## Lösung

Wenden Sie den in diesem Artikel bereitgestellten Patch an.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[B2B-709-composer.patch](assets/B2B-709-composer.patch.zip)

Der Patch kann auch in den Formaten `.git` und `.composer` heruntergeladen werden, die auf der Seite [Adobe Commerce-Downloads](https://magento.com/tech-resources/download) unter **Patches** in der linken Spaltennavigation verfügbar sind. Suchen Sie nach XXX Patch.

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches in unserer Support-Wissensdatenbank.
