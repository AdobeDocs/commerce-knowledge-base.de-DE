---
title: Patch für Amazon Pay-out-Problem in Adobe Commerce 2.3.5-p1
description: Dieser Patch behebt das Problem, dass es nicht möglich ist, eine Zahlungsmethode beim Checkout "Review & Payments"-Schritt vom Zahlungswidget zu ändern, während Sie mit Amazon Pay in Adobe Commerce auschecken.
exl-id: a241f67f-019c-4ff2-a5ad-e7dc71639768
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Patch für Amazon Pay-out-Problem in Adobe Commerce 2.3.5-p1

Dieser Patch behebt das Problem, dass es nicht möglich ist, eine Zahlungsmethode beim Checkout &quot;Review &amp; Payments&quot;-Schritt vom Zahlungswidget zu ändern, während Sie mit Amazon Pay in Adobe Commerce auschecken.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur-Version 2.3.5-p1
* Adobe Commerce On-Premise Version 2.3.5-p1

## Problem

Wenn ein Käufer mit Amazon Pay auscheckt, sich anmeldet, zum Zahlungsschritt übergeht und versucht, seine Kreditkarte über das Zahlungswidget zu ändern, wird eine Fehlermeldung angezeigt. Der Checkout kann nicht abgeschlossen werden, wenn der Käufer den Fehler ignoriert und mit dem Checkout fortfährt.

Um dieses Problem zu beheben und den Fehler zu entfernen, haben wir einen [Patch](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip) erstellt.

<u>Zu reproduzierende Schritte</u>:

1. Starten Sie mit Amazon Pay zum Checkout.
1. Melden Sie sich als Amazon Pay-Kunde an.
1. Wählen Sie die Versandmethode aus und fahren Sie mit dem Zahlungsschritt fort.
1. Versuchen Sie, die Kreditkarte in eine andere umzuwandeln.

<u>Erwartetes Ergebnis</u>: Eine andere Kreditkarte wird als Zahlungsmethode ohne Fehler ausgewählt.

<u>Tatsächliches Ergebnis</u>: Die Fehlermeldung wird angezeigt: *&quot;Wenden Sie sich an diesen Händler, um Hilfe beim Abschließen Ihrer Bestellung zu erhalten.&quot;*

## Lösung

[Wenden Sie den Patch](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip) unten an.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[Laden Sie BUNDLE-2554\_EE\_2.3.5-p1.composer.patch herunter](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip)

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce auf Cloud-Infrastruktur-Version 2.3.5-p1
* Adobe Commerce On-Premise Version 2.3.5-p1

Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce auf Cloud-Infrastruktur, Version 2.3.5
* Adobe Commerce On-Premise Version 2.3.5

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches in unserer Support-Wissensdatenbank.

## Attached Files
