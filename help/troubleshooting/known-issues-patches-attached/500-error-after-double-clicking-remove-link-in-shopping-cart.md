---
title: '"500-Fehler" nach Doppelklick auf Link im Warenkorb entfernen'
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce-Problem in der Cloud-Infrastruktur 2.2.0, das darauf zurückzuführen ist, dass Kunden beim Versuch, ein zweimal gekauftes Warenkorbelement zu entfernen, einen Fehler erhalten (durch Doppelklicken auf den Link *Entfernen* oder durch Klicken auf das Element auf verschiedenen Registerkarten).
exl-id: 927cf681-febf-42cc-8db5-469bcf8f2012
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# &quot;500-Fehler&quot;nach Doppelklicken auf Link im Warenkorb entfernen

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce-Problem in der Cloud-Infrastruktur 2.2.0, das darauf zurückzuführen ist, dass Kunden beim Versuch, ein zweimal gekauftes Warenkorbelement zu entfernen, einen Fehler erhalten (durch Doppelklicken auf den Link *Entfernen* oder durch Klicken auf das Element auf verschiedenen Registerkarten).

## Problem

Wenn Kunden auf den Link *Entfernen* im Warenkorb doppelklicken und versuchen, ein Produkt aus dem Warenkorb zu entfernen, erhalten sie eine leere Seite mit der folgenden Fehlermeldung: *&quot;Diese Seite funktioniert nicht. HTTP-FEHLER 500&quot;.* Das gleiche Problem tritt auf, wenn ein Kunde zwei Browser-Registerkarten mit der Warenkorbseite öffnet und das Produkt zuerst auf einer Registerkarte und dann auf der zweiten entfernt.

<u>Zu reproduzierende Schritte</u> :

1. Fügen Sie ein Produkt zum Warenkorb auf der Storefront hinzu.
1. Navigieren Sie zur Warenkorbseite.
1. Doppelklicken Sie auf den Link Entfernen .

ODER

1. Fügen Sie ein Produkt zum Warenkorb auf der Storefront hinzu.
1. Navigieren Sie zur Warenkorbseite.
1. Öffnen Sie eine neue Browser-Registerkarte und navigieren Sie zur Einkaufswagenseite (dasselbe Produkt).
1. Entfernen Sie das Produkt aus dem Warenkorb.
1. Öffnen Sie die zweite Registerkarte und entfernen Sie das Produkt erneut.

<u>Erwartetes Ergebnis</u> : Das Produkt wird ohne Fehler aus dem Warenkorb entfernt.

<u>Tatsächliches Ergebnis</u> : Das Produkt wird mit dem Fehler &quot;*&quot;entfernt. Diese Seite funktioniert nicht. HTTP-FEHLER 500&quot;* Fehlermeldung.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-8623\_EE\_2.2.0\_v1.composer.patch herunterladen](assets/MDVA-8623_EE_2.2.0_v1.composer.patch.zip)

## Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce auf Cloud-Infrastruktur 2.2.0

Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce auf Cloud-Infrastruktur 2.2.1 - 2.2.5
* Adobe Commerce vor Ort 2.2.0 - 2.2.5

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches in unserer Support-Wissensdatenbank.

## Attached Files
