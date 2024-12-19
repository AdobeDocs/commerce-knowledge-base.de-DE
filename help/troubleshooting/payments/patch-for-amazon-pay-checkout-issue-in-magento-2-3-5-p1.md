---
title: Patch für das Problem mit der gebührenpflichtigen Kasse von Amazon in Adobe Commerce 2.3.5-p1
description: Dieser Patch behebt das Problem, dass eine Zahlungsmethode beim Checkout-Schritt „Überprüfung und Zahlungen“ über das Zahlungs-Widget nicht geändert werden kann, während in Adobe Commerce mit Amazon Pay ausgecheckt wird.
exl-id: a241f67f-019c-4ff2-a5ad-e7dc71639768
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Patch für das Problem mit der gebührenpflichtigen Kasse von Amazon in Adobe Commerce 2.3.5-p1

Dieser Patch behebt das Problem, dass eine Zahlungsmethode beim Checkout-Schritt „Überprüfung und Zahlungen“ über das Zahlungs-Widget nicht geändert werden kann, während in Adobe Commerce mit Amazon Pay ausgecheckt wird.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, Version 2.3.5-p1
* Adobe Commerce On-Premise, Version 2.3.5-p1

## Problem

Wenn ein Käufer mit Amazon Pay auscheckt, sich anmeldet, mit dem Zahlungsschritt fortfährt und versucht, seine Zahlungskreditkarte über das Zahlungs-Widget zu ändern, wird eine Fehlermeldung angezeigt. Der Checkout kann nicht abgeschlossen werden, wenn der Käufer den Fehler ignoriert und mit dem Checkout fortfährt.

Um dieses Problem zu beheben und den Fehler zu entfernen, haben wir einen [Patch](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip) erstellt.

<u>Schritte zur Reproduktion</u>:

1. Checkout mit Amazon Pay starten.
1. Melden Sie sich als Amazon Pay-Kunde an.
1. Wählen Sie die Versandart und fahren Sie mit dem Zahlungsschritt fort.
1. Versuchen Sie, eine andere Kreditkarte zu wählen.

<u>Erwartetes Ergebnis</u>: Als Zahlungsmethode wird ohne Fehler eine andere Kreditkarte ausgewählt.

<u>Tatsächliches Ergebnis</u>: Die Fehlermeldung wird angezeigt: *„Wenden Sie sich an diesen Händler, um Hilfe beim Abschließen Ihrer Bestellung zu erhalten.“*

## Lösung

[Wenden Sie das Pflaster unten ](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip).

## Fleck

Der Patch ist diesem Artikel beigefügt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[BUNDLE-2554\_EE\_2.3.5-p1.composer.patch herunterladen](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip)

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde erstellt für:

* Adobe Commerce auf Cloud-Infrastruktur, Version 2.3.5-p1
* Adobe Commerce On-Premise, Version 2.3.5-p1

Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (kann das Problem jedoch nicht beheben):

* Adobe Commerce auf Cloud-Infrastruktur Version 2.3.5
* Adobe Commerce On-Premise, Version 2.3.5

## Anbringen des Pflasters

Anweisungen [ Sie in unserer Support](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)Wissensdatenbank unter „Anwenden eines von Adobe Commerce bereitgestellten Composer-Patches“.

## Angehängte Dateien
