---
title: Problem mit leerem Warenkorb beim mehrfachen Klick auf den Kassengang aus dem Mini-Warenkorb
description: Dieser Artikel enthält einen Patch für ein bekanntes Adobe Commerce 2.2.3-Problem, bei dem ein Warenkorb leer ist, nachdem Kunden mehrmals im Mini-Warenkorb auf **Go to Checkout** geklickt haben.
exl-id: 06b82c91-8998-4e7b-9fc0-671c9b2a2d3f
feature: Checkout, Orders, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# Problem mit leerem Warenkorb beim mehrfachen Klick auf den Kassengang aus dem Mini-Warenkorb

Dieser Artikel enthält einen Patch für ein bekanntes Adobe Commerce 2.2.3-Problem, bei dem ein Warenkorb leer ist, nachdem Kunden mehrmals im Mini-Warenkorb auf **Gehe zur Kasse** geklickt haben.

## Problem

Kunden fügen Produkte zum Warenkorb hinzu und versuchen, einen Kauf abzuschließen, indem sie mehrmals auf die Schaltfläche **Zum Checkout wechseln** klicken. Wenn sie jedoch zum Warenkorb gehen, ist der Warenkorb leer. Der Mini-Warenkorb zeigt möglicherweise noch Produkte an.

<u>Zu reproduzierende Schritte</u> :

1. Öffnen Sie eine Produktseite auf der Storefront.
1. Produkte zum Warenkorb hinzufügen.
1. Klicken Sie im Mini-Warenkorb mehrmals auf **Zum Checkout gehen** .

<u>Erwartetes Ergebnis</u> :

Der Warenkorb enthält alle von Ihnen hinzugefügten Produkte.

<u>Tatsächliches Ergebnis</u> :

Sie haben keine Artikel in Ihrem Warenkorb.

## Patch

Die Patches sind diesem Artikel beigefügt. Um einen Patch herunterzuladen, scrollen Sie nach unten zum Ende des Artikels und klicken Sie auf den gewünschten Dateinamen oder auf einen der folgenden Links:

[MDVA-10441\_EE\_2.2.3\_v3.composer.patch herunterladen](assets/MDVA-10441_EE_2.2.3_v3.composer.patch.zip)

[MDVA-17078\_EE\_2.2.5\_COMPOSER\_v1.patch herunterladen](assets/MDVA-17078_EE_2.2.5_COMPOSER_v1.patch.zip)

### Kompatible Adobe Commerce-Versionen

Die Patches wurden für Folgendes erstellt:

* Adobe Commerce On-Premise 2.2.3 (Datei `MDVA-10441_EE_2.2.3_v3.composer.patch`)
* Adobe Commerce in Cloud-Infrastruktur 2.2.5 (`MDVA-17078_EE_2.2.5_COMPOSER_v1.patch` -Datei)

Der Patch `MDVA-10441_EE_2.2.3_v3.composer.patch` ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce auf Cloud-Infrastrukturversionen von 2.2.1 bis 2.2.5
* Adobe Commerce-Versionen vor Ort von 2.2.1 bis 2.2.5

Der Patch `MDVA-17078_EE_2.2.5_COMPOSER_v1.patch` ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce 2.2.5

## Anwenden eines Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches in unserer Support-Wissensdatenbank.

## Attached Files
