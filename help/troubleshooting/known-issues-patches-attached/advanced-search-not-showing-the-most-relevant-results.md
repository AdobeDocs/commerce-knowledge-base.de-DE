---
title: Erweiterte Suche ohne relevanteste Ergebnisse
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce-Problem, bei dem die erweiterte Suche nicht zuerst die relevantesten Ergebnisse anzeigt.
exl-id: 88f0782d-ba7d-4f19-9761-7894d978d334
feature: Search
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Erweiterte Suche ohne relevanteste Ergebnisse

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce-Problem, bei dem die erweiterte Suche nicht zuerst die relevantesten Ergebnisse anzeigt.

## Betroffene Versionen {#Advancedsearchnotshowingmostrelevantresults-Affectedversions}

* Adobe Commerce (alle Bereitstellungsoptionen) 2.x.x
* Magento Open Source 2.x.x

## Problem {#Advancedsearchnotshowingmostrelevantresults-Description}

Die erweiterte Suchfunktion gibt nicht zuerst die relevantesten Ergebnisse zurück, wie es bei der Schnellsuche der Fall ist. Das Problem hängt nicht vom ausgewählten Suchmaschinentyp ab.

<u>Zu reproduzierende Schritte:</u>

1. Suchen Sie im Schaufenster nach &quot;Angepasste Jacke&quot;.
1. Beachten Sie &quot;Orion Two-Tone Fitted Jacket&quot; ist das erste Ergebnis.
1. Gehen Sie zur erweiterten Suche und suchen Sie im Namensfeld nach &quot;Angepasste Jacke&quot;.

<u>Erwartetes Ergebnis:</u>

Die &quot;Orion Two-Tone Fitted Jacket&quot; ist das erste Ergebnis bei der Verwendung der erweiterten Suche, als relevantestes Ergebnis.

<u>Tatsächliches Ergebnis:</u>

Die &quot;Orion Two-Tone Fitted Jacket&quot; ist nicht das erste Ergebnis, obwohl es am relevantesten ist.

## Lösung {#Advancedsearchnotshowingmostrelevantresults-Solution}

Um das Problem zu lösen, wenden Sie den Patch an, der diesem Artikel beigefügt ist. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-7256\_EE\_2.1.7\_v1.composer.patch herunterladen](assets/MDVA-7256_EE_2.1.7_v1.composer.patch.zip)

Der Patch fügt die Implementierung zum Sortieren nach Relevanz für erweiterte Suchergebnisse als standardmäßiges Sortierungsfeld hinzu.

Der Patch ist mit allen betroffenen Versionen und Editionen kompatibel.

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches in unserer Support-Wissensdatenbank.

## Attached files
