---
title: Überarbeitete Patches für Google Maps-Zugriffsverluste in allen Adobe Commerce-Versionen
description: Dieser Artikel bietet eine Fehlerbehebung für Adobe Commerce-Händler, die mit keiner der neuesten  [!DNL Google Maps]  ab Version 3.54 kompatibel sind.
feature: Install, Upgrade
role: Developer
exl-id: 6151e89a-3190-40cb-b599-94ae5530488b
source-git-commit: d7e58d6a9ed8e9b369ea41165cbdd6b362e40824
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Überarbeitete Patches für [!DNL Google Maps] Zugriffsverlust in allen Adobe Commerce-Versionen

Dieser Artikel bietet eine Fehlerbehebung für Adobe Commerce-Händler, die mit keiner aktuellen [!DNL Google Maps] ab Version 3.54 kompatibel sind. Mit dieser Fehlerbehebung wird das Problem behoben, dass Adobe Commerce-Händler in keiner Version von Adobe Commerce mehr Zugriff auf [!DNL Google Maps] haben.

## Betroffene Versionen und Produkte

* Versionen von Adobe Commerce und/oder anderen verwendeten Technologien.
* Adobe Commerce *2.4.4* - *2.4.7* auf Cloud- und On-Premise-Versionen.

## Problem

Am *14. Juni* erreichte [!DNL Google Maps] Version *3.53* das Ende des Lebenszyklus und wurde von [!DNL Google] abgeschaltet.

Weitere Informationen finden Sie unter [[!DNL Google Maps Platform: Maps JavaScript API]](https://developers.google.com/maps/documentation/javascript/versions#documentation-for-the-api-versions).

Adobe Commerce war mit keiner der aktuellen [!DNL &#x200B; Google Maps] ab Version 3.54 kompatibel.

Die Inkompatibilität wurde durch ältere `prototype.js script` verursacht, die durch geladen wurden, `lib/web/legacy-build.min.js` die native Funktion Array.from überschreibt, was zu einem direkten Konflikt mit [!DNL &#x200B; Google Maps] API führt.

Siehe [[!DNL Google Maps: JS Best Practices]](https://developers.google.com/maps/documentation/javascript/best-practices).

<u>Schritte zur Reproduktion</u> :

1. Klicken Sie auf **[!UICONTROL Content]** > **[!UICONTROL Pages]** > und wählen Sie eine **[!UICONTROL New Page]** aus.
1. Erweitern Sie den Inhaltsbaustein und klicken Sie auf die Schaltfläche **[!DNL PageBuilder]** bearbeiten .
1. Ziehen Sie den Block Inhalt zuordnen aus dem Menü **[!DNL PageBuilder]** auf die Seite.

<u>Erwartetes Ergebnis:</u>

[!DNL Google Maps] sollte erwartungsgemäß funktionieren.

<u> Tatsächliches Ergebnis:</u>

Wenn Sie den Block „Inhalt zuordnen“ aus **[!DNL PageBuilder]** Menü auf die Seite ziehen, wird eine Fehlermeldung wie *angezeigt. Etwas ist schiefgelaufen“* wird angezeigt.

## Lösung

* Alle Händler, die mit einer Patch-Version 2.4.4, 2.4.5, 2.4.6 oder 2.4.7 arbeiten, sollten diese entsprechenden Patches auf ihre Version anwenden.

## Fleck

Verwenden Sie je nach Adobe Commerce-Version die folgenden angehängten Patches:

**Für Versionen 2.4.4:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Für Versionen 2.4.5:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Für Versionen 2.4.6:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Für Versionen 2.4.7:**
[ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip)

**Bitte beachten**

Dieses Problem wird im Rahmen der Patch-Versionen, die nur für die Sicherheit im August gelten, dauerhaft behoben:
2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10

## Verwandtes Lesen

[Wie man einen Composer Patch von Adobe aufbringt](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)
