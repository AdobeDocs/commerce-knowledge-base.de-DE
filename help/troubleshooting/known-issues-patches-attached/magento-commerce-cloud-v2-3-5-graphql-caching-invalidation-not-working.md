---
title: Adobe Commerce auf Cloud-Infrastruktur v2.3.5 GraphQL-Cache-Invalidierung nicht funktioniert
description: Dieser Artikel enthält einen Patch für das Problem, bei dem die GraphQL-Anfrage "GET"veraltete Informationen zurückgibt, wenn der Kunde die Produktinformationen ändert.
exl-id: 10ae52bd-e71a-42e3-9600-7a9713903815
feature: GraphQL, Cache, Categories, Cloud, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Adobe Commerce auf Cloud-Infrastruktur v2.3.5 GraphQL-Cache-Invalidierung nicht funktioniert

Dieser Artikel enthält einen Patch für das Problem, bei dem die GraphQL `GET`-Anfrage veraltete Informationen zurückgibt, wenn der Kunde die Produktinformationen ändert.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur v2.3.5.

## Problem

GraphQL-Anforderungen werden von Fastly zwischengespeichert und die zwischengespeicherte Version wird für jede nachfolgende Anforderung von Fastly abgerufen. Wenn ein Produkt im Adobe Commerce-Backend erneut gespeichert wird, sollte der schnelle Cache invalidiert werden, wenn ein Produkt aktualisiert wird. Sie bleibt jedoch gültig.

<u>Zu reproduzierende Schritte</u>:

1. Trigger Sie die folgende GraphQL-Anfrage, um Produkte für bestimmte Kategorien abzurufen, z. B.:
   <pre><magento2-server>
    </pre>
1. Speichern Sie eines der von der obigen Anfrage abgerufenen Produkte im Commerce-Admin erneut.
1. Trigger der Anfrage erneut.

<u>Erwartete Ergebnisse</u>:

Die Kopfzeile `X-Cache` enthält `MISS`.

<u>Tatsächliche Ergebnisse</u>:

Die Kopfzeile `X-Cache` enthält `HIT`, was bedeutet, dass die Antwort zwischengespeichert wird.

## Lösung

Deaktivieren Sie den GraphQL-Produkt-Cache mit dem in diesem Artikel bereitgestellten Patch.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-28559\_EE\_2.3.5-p1\_COMPOSER\_v1.patch](assets/MDVA-28559_EE_2.3.5-p1_v1.composer.patch.zip)

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce auf Cloud-Infrastruktur v2.3.5

Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce auf Cloud-Infrastruktur v2.4.0
* Adobe Commerce On-Premise v2.4.0
* Adobe Commerce auf Cloud-Infrastruktur v2.3.5-p2
* Adobe Commerce On-Premise v2.3.5-p2
* Adobe Commerce auf Cloud-Infrastruktur v2.3.5-p1
* Adobe Commerce On-Premise v2.3.5-p1
* Adobe Commerce On-Premise v2.3.5
* Adobe Commerce auf Cloud-Infrastruktur v2.3.4-p2
* Adobe Commerce On-Premise v2.3.4-p2
* Adobe Commerce auf Cloud-Infrastruktur v2.3.4
* Adobe Commerce On-Premise v2.3.4
* Adobe Commerce On-Premise v2.3.3-p1
* Adobe Commerce lokal v2.3.3

## Anwenden des Pflasters

Anweisungen zum Anwenden eines Composer-Patches finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches.

## Attached files
