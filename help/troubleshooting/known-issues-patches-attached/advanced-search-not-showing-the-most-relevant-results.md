---
title: Erweiterte Suche zeigt nicht die relevantesten Ergebnisse an
description: In diesem Artikel finden Sie einen Patch für das bekannte Adobe Commerce-Problem, bei dem die erweiterte Suche nicht zuerst die relevantesten Ergebnisse anzeigt.
exl-id: 88f0782d-ba7d-4f19-9761-7894d978d334
feature: Search
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Erweiterte Suche zeigt nicht die relevantesten Ergebnisse an

In diesem Artikel finden Sie einen Patch für das bekannte Adobe Commerce-Problem, bei dem die erweiterte Suche nicht zuerst die relevantesten Ergebnisse anzeigt.

## Betroffene Versionen {#Advancedsearchnotshowingmostrelevantresults-Affectedversions}

* Adobe Commerce (alle Bereitstellungsoptionen) 2.x.x
* Magento Open Source 2.x.x

## Problem {#Advancedsearchnotshowingmostrelevantresults-Description}

Die erweiterte Suchfunktion gibt nicht zuerst die relevantesten Ergebnisse zurück, wie es die Schnellsuche tut. Das Problem hängt nicht vom ausgewählten Suchmaschinentyp ab.

<u>Schritte zur Reproduktion:</u>

1. Navigieren Sie in der Storefront zur Schnellsuche und suchen Sie nach „Fitted Jacket“.
1. Hinweis „Orion Two-Tone Fitted Jacket“ ist das erste Ergebnis.
1. Gehen Sie zur erweiterten Suche und suchen Sie im Namensfeld nach „Fitted Jacket“.

<u>Erwartetes Ergebnis:</u>

Die „Orion Two-Tone Fitted Jacket“ ist das erste Ergebnis bei der Verwendung der erweiterten Suche, als das relevanteste Ergebnis.

<u>Tatsächliches Ergebnis:</u>

Die „Orion Two-Tone Fitted Jacket“ ist nicht das erste Ergebnis, aber das wichtigste.

## Lösung {#Advancedsearchnotshowingmostrelevantresults-Solution}

Um das Problem zu beheben, wenden Sie den Patch an, der diesem Artikel beigefügt ist. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-7256\_EE\_2.1.7\_v1.composer.patch herunterladen](assets/MDVA-7256_EE_2.1.7_v1.composer.patch.zip)

Der Patch fügt die Implementierung für die Sortierung nach Relevanz für erweiterte Suchergebnisse als standardmäßiges Sortierfeld hinzu.

Der Patch ist mit allen betroffenen Versionen und Editionen kompatibel.

## Anbringen des Pflasters

Anweisungen finden Sie unter [So wenden Sie einen von Adobe bereitgestellten Composer-Patch ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) unserer Support-Wissensdatenbank an.

## Angehängte Dateien
