---
title: "Adobe Commerce 2.3.5, 2.3.5-p1 Patch: Problem mit Länderzahlungen"
description: Dieser Patch behebt ein Problem in Adobe Commerce, bei dem der Store-Front-Checkout-Workflow keine Zahlungsmethode anzeigte, die für bestimmte Länder aktiviert wurde, mit Ausnahme von Klarna und Amazon Pay.
exl-id: e205e35e-9ffe-4826-b951-3a3caf1e0621
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Adobe Commerce 2.3.5, 2.3.5-p1-Patch: Problem mit Länderzahlungen

Dieser Patch behebt ein Problem in Adobe Commerce, bei dem der Store-Front-Checkout-Workflow keine Zahlungsmethode anzeigte, die für bestimmte Länder aktiviert wurde, mit Ausnahme von Klarna und Amazon Pay.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.3.5 und 2.3.5-p1
* Adobe Commerce vor Ort 2.3.5 und 2.3.5-p1

## Problem

Wenn einem Geschäft Amazon Pay und eine andere Zahlung zugewiesen ist und eines dieser Länder und Zahlungsmethoden ausgewählt ist, sind die Zahlungsmethode und die Bestellschaltflächen nicht sichtbar.

Eine Aktualisierung der Webseite ist eine Problemumgehung.

Um dieses Problem zu beheben und den Fehler zu entfernen, haben wir eine [Patch](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip).

<u>Voraussetzungen</u>:

* Ein einfaches Produkt wird erstellt.
* **Überprüfen/Monatsbestellung** ist nur für bestimmte Länder aktiviert (unter **Store** > **Konfiguration** > **Vertrieb** > **Zahlungsmethoden**).

* Beispiel: Zahlung aus den betreffenden Ländern = spezifische Länder
* Beispiel: Zahlungen aus bestimmten Ländern = Vereinigtes Königreich

<u>Zu reproduzierende Schritte</u>:

1. Besuchen Sie die Storefront als Gast.
1. Fügen Sie dem Warenkorb ein einfaches Produkt hinzu.
1. Wechseln Sie zur Kasse.
1. Füllen Sie das Formular mit gültigen Daten aus.

   * Land = *Vereinigte Staaten*

1. Wählen Sie die Versandrate aus und klicken Sie auf **Nächste**.

   * Der Zahlungsschritt wird geöffnet.
   * Es gibt keine Zahlungen.
   * Nachricht: **Keine Zahlungsmethode verfügbar.**
   * Es gibt keine **Bestellung platzieren** Schaltfläche.

1. Gehen Sie zurück zu **Versandschritt** und ändern Sie den Wert in:

   * Land = *Vereinigtes*

1. Wählen Sie die Versandrate aus und klicken Sie auf **Nächste**.

<u>Erwartetes Ergebnis</u>:

Der Zahlungsschritt wird geöffnet.

* **Bargeld bei Lieferung** angezeigt.
* **Überprüfen/Monatsbestellung** angezeigt.
* Die **Bestellung platzieren** angezeigt.

<u>Tatsächliches Ergebnis</u>:

Der Zahlungsschritt wird geöffnet.

* Es gibt keine Zahlungen.
* Nachricht: *Keine Zahlungsmethode verfügbar.*
* Es gibt keine **Bestellung platzieren** Schaltfläche.

## Lösung

[Wenden Sie den Patch an](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip) unten.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[Laden Sie BUNDLE-2546\_EE\_2.3.5-p1.composer.patch herunter](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip)

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce auf Cloud-Infrastruktur 2.3.5 und 2.3.5-p1
* Adobe Commerce vor Ort 2.3.5 und 2.3.5-p1

Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce-Versionen 2.3.4-p2 - 2.2.6

## Anwenden des Pflasters

Siehe [Anwenden eines von Adobe Commerce bereitgestellten Komponentenpatches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in unserer Support-Wissensdatenbank für Anleitungen.

## Attached Files
