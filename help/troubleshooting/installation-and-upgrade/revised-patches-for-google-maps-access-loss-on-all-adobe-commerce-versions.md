---
title: Überarbeitete Patches für Google Maps-Zugriffsverluste für alle Adobe Commerce-Versionen
description: "Dieser Artikel enthält eine Fehlerbehebung für Adobe Commerce-Händler, die nicht mit aktuellen [!DNL Google Maps] Versionen ab Version 3.54 kompatibel sind."
feature: Install, Upgrade
role: Developer
source-git-commit: cf235c2fdd7a36d7e3b126de35c51e6711cd3845
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Überarbeitete Patches für den [!DNL Google Maps]-Zugriffsverlust bei allen Adobe Commerce-Versionen

Dieser Artikel enthält eine Fehlerbehebung für Adobe Commerce-Händler, die nicht mit aktuellen [!DNL Google Maps]-Versionen ab Version 3.54 kompatibel sind. Mit dieser Korrektur wird das Problem behoben, bei dem Adobe Commerce-Händler in keiner Version von Adobe Commerce mehr Zugriff auf [!DNL Google Maps] haben.

## Betroffene Versionen und Produkte

* Versionen von Adobe Commerce und/oder anderen verwendeten Technologien.
* Adobe Commerce *2.4.4* - *2.4.7* für Cloud- und On-Premises-Versionen.

## Problem

Am *14. Juni 2024* [!DNL Google Maps] Version *3,53* erreichte das Ende des Lebenszyklus und wurde um [!DNL Google] abgeschaltet.

Weitere Informationen finden Sie unter [[!DNL Google Maps Platform: Maps JavaScript API]](https://developers.google.com/maps/documentation/javascript/versions#documentation-for-the-api-versions).

Adobe Commerce war nicht mit aktuellen [!DNL  Google Maps]-Versionen ab Version 3.54 kompatibel.

Die Inkompatibilität wurde durch das veraltete `prototype.js script` verursacht, das durch `lib/web/legacy-build.min.js` geladen wird, die native Array.from-Funktion außer Kraft setzt, was zu einem direkten Konflikt mit der [!DNL  Google Maps]-API führt.

Siehe [[!DNL Google Maps: JS Best Practices]](https://developers.google.com/maps/documentation/javascript/best-practices).

<u>Zu reproduzierende Schritte</u> :

1. Klicken Sie auf **[!UICONTROL Content]** > **[!UICONTROL Pages]** > und wählen Sie eine **[!UICONTROL New Page]** aus.
1. Erweitern Sie den Inhaltsbaustein und klicken Sie auf die Schaltfläche **[!DNL PageBuilder]** bearbeiten .
1. Ziehen Sie den Baustein Inhalt zuordnen aus dem Menü **[!DNL PageBuilder]** auf die Seite.

<u>Erwartetes Ergebnis:</u>

[!DNL Google Maps] sollte erwartungsgemäß funktionieren.

<u> Tatsächliches Ergebnis:</u>

Wenn Sie den Baustein Inhalt zuordnen aus dem Menü **[!DNL PageBuilder]** auf der Seite ablegen, wird eine Fehlermeldung wie *&quot;Entschuldigung! Etwas ist schiefgelaufen&quot;* wird angezeigt.

## Lösung

* Alle Händler in Patch-Versionen 2.4.4, 2.4.5, 2.4.6 oder 2.4.7 sollten diese Patches auf ihre Version anwenden.

## Patch

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

Dieses Problem wird im Rahmen der Sicherheits-Patch-Versionen vom August dauerhaft behoben:
2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10

## Verwandte Informationen

[Anwenden eines von Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento) bereitgestellten Composer-Patches