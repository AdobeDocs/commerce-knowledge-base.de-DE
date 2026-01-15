---
title: Adobe Commerce 2.4.0 B2B-Admin kann kein konfigurierbares Produkt zum Angebot hinzufügen
description: In diesem Artikel wird über ein bekanntes Problem in Commerce Admin bei der Verwaltung eines B2B-Angebots gesprochen. Es ist nicht möglich, dem Angebot ein konfigurierbares Produkt **SKU** hinzuzufügen. Wenn Sie auf die Schaltfläche **Zum Angebot hinzufügen** klicken, bleibt die **Angebot**-Bearbeitungsseite hängen und Sie können das Produkt nicht konfigurieren und Änderungen speichern. Dieses Problem tritt auch in Admin auf, wenn ein Produkt per **SKU** zu einer Bestellung oder ein Produkt per **SKU** in **Erweiterter Checkout** hinzugefügt wird (**Admin** &gt; **Kunden** &gt; **Alle Kunden** &gt; **Kundenbearbeitung** &gt; **Warenkorb verwalten**). Dieses Problem wird in einem Patch für Adobe Commerce 2.4.1 behoben.
exl-id: 73f7231b-b496-4250-b9e2-29427c772d56
feature: Admin Workspace, B2B, Catalog Management, Configuration, Products, Quotes
role: Developer
source-git-commit: 05297c82b292b8ccc88018c58e991bd3a32d6ffa
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 B2B-Admin kann kein konfigurierbares Produkt zum Angebot hinzufügen

In diesem Artikel wird über ein bekanntes Problem in Commerce Admin bei der Verwaltung eines B2B-Angebots gesprochen. Es ist nicht möglich, dem Angebot ein konfigurierbares Produkt **SKU** hinzuzufügen. Wenn Sie auf die Schaltfläche **Zum Angebot hinzufügen** klicken, bleibt die **Angebot**-Bearbeitungsseite hängen und Sie können das Produkt nicht konfigurieren und Änderungen speichern. Dieses Problem tritt auch in Admin auf, wenn ein Produkt **SKU** zu einer Bestellung hinzugefügt wird oder wenn ein Produkt **SKU** in **Erweiterter Checkout** hinzugefügt wird (**Admin** > **Kunden** > **Alle Kunden** > **Kundenbearbeitung** > **Warenkorb verwalten**). Dieses Problem wird in einem Patch für Adobe Commerce 2.4.1 behoben.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.4.0
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

## Problem

<u>Voraussetzungen</u>

* Adobe Commerce 2.4.0 ist installiert.
* B2B ist installiert.
* Legen Sie B2B-Funktionen auf **Unternehmen aktivieren =** *Ja* , **Freigegebenen Katalog aktivieren =** *Nein* und **** B2B-Angebot aktivieren =*Ja* fest.
* Kundenkonto erstellen.
* Erstellen Sie ein Unternehmenskonto mit dem zuvor erstellten Kunden als Unternehmensadministrator.
* Erstellen Sie ein einfaches Produkt (Beispiel: name &amp; **SKU** = TEST SIMPLE 1), das nicht **Standard (Allgemein) zugewiesen**.
* Fordern Sie vom Administrator des Unternehmens ein Angebot mit dem oben erstellten einfachen Produkt an (Beispiel: TEST SIMPLE 1).

<u>Schritte zur Reproduktion</u>

1. Zum Commerce Admin-Bedienfeld.
1. Gehen Sie zu **Verkauf > Angebote**.
1. Öffnen Sie das **Zitat**.
1. Klicken Sie auf **Schaltfläche „Produkt nach SKU hinzufügen**.
1. Geben Sie **SKU** eines anderen Produkts (Beispiel: TEST SIMPLE 2) in das Eingabefeld **SKU eingeben** ein.
1. Geben Sie eine gültige Menge in das Eingabefeld **Menge** ein.
1. Klicken Sie auf **Schaltfläche „Zum Angebot hinzufügen**.

<u>Erwartete Ergebnisse</u>

* Das Raster **Produkte, die nicht zum Angebot hinzugefügt wurden** mit dem Namen und **SKU** des erstellten Produkts wird erwartungsgemäß angezeigt.
* Nachdem das Produkt konfiguriert wurde, kann es der Administrator dem **Angebot“ hinzufügen** indem er erwartungsgemäß auf die Schaltfläche **Produkte zum Angebot hinzufügen** klickt.

<u>Tatsächliche Ergebnisse</u>

* Das Raster **Produkte, die nicht zum Angebot hinzugefügt wurden** mit dem Namen und **SKU** des erstellten Produkts wird nicht angezeigt.
* Die **Zitat**-Seite wurde nicht geladen.

## Empfehlung

Derzeit gibt es für dieses Problem mit der B2B-Angebotsbearbeitung keine Problemumgehung. Für die Verwaltung von Bestellungen und Warenkorb ist es jedoch möglich, Produkte aus der **Produktliste** auszuwählen, anstatt sie per **SKU** hinzuzufügen. Ein Patch zur Behebung des Problems wird für Adobe Commerce 2.4.1 verfügbar sein, das im 4. Quartal 2020 veröffentlicht werden soll.

