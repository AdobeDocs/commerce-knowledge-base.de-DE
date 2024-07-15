---
title: Checkout-Seiten werden nicht geladen, wenn die Anzeigensperre aktiviert ist
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce-Problem in der Cloud-Infrastruktur 2.2.2, das mit dem Fehler zusammenhängt, Checkout-Seiten zu laden, der durch uBlock oder andere Anzeigensperren verursacht wurde.
exl-id: fe718f21-df23-4ab1-a6b0-03bad4d7095d
feature: Checkout, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# Checkout-Seiten werden nicht geladen, wenn die Anzeigensperre aktiviert ist

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce-Problem in der Cloud-Infrastruktur 2.2.2, das mit dem Fehler zusammenhängt, Checkout-Seiten zu laden, der durch uBlock oder andere Anzeigensperren verursacht wurde.

## Problem

Wenn Google Analytics für den Store aktiviert ist und ein Kunde mit installiertem Block oder einem anderen Anzeigenblocker zum Checkout übergeht, wird das Laden der `trackingCode.js` -Datei verhindert und RequireJS unterbricht den JS-Ausführungsfluss. Dies führt zu Problemen beim Laden der Checkout-Seite.

<u>Zu reproduzierende Schritte</u> :

Voraussetzungen: Ein Werbedruck muss im Browser installiert und aktiv sein.

1. Aktivieren und konfigurieren Sie in Commerce Admin die Google Analytics-Funktion.
1. Öffnen Sie eine Produktseite auf der Storefront.
1. Produkte zum Warenkorb hinzufügen.
1. Klicken Sie auf den Link **Zum Checkout wechseln** .

<u>Erwartetes Ergebnis</u>: Checkout-Seite wird geladen und der Kunde kann den Checkout abschließen.

<u>Tatsächliches Ergebnis</u>: Die Seite &quot;Auschecken&quot;wird nicht geladen. Das Ladegerät verschwindet nie.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-9353\_EE\_2.2.2\_v1.composer.patch herunterladen](assets/MDVA-9353_EE_2.2.2_v1.composer.patch.zip)

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce in Cloud-Infrastruktur 2.2.2

Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce auf Cloud-Infrastruktur von 2.1.0 bis 2.1.14
* Adobe Commerce für Cloud-Infrastruktur von 2.2.0 bis 2.2.1 und 2.2.3 bis 2.2.5
* Adobe Commerce vor Ort von 2.1.0 bis 2.1.14
* Adobe Commerce vor Ort von 2.2.0 bis 2.2.5

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches in unserer Support-Wissensdatenbank.

## Nützliche Links

* [Das Problem, das auf GitHub besprochen wurde](https://github.com/magento/magento2/pull/13061)

## Attached Files
