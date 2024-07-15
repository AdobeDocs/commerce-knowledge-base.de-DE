---
title: Adobe Commerce 2.4.0 B2B Admin kann kein konfigurierbares Produkt zum Anführungszeichen hinzufügen
description: In diesem Artikel wird über ein bekanntes Problem in Commerce Admin bei der Verwaltung eines B2B-Zitats gesprochen. Es ist nicht möglich, ein konfigurierbares Produkt durch **SKU** zum Angebot hinzuzufügen. Wenn Sie auf die Schaltfläche **Zu Anführungszeichen hinzufügen** klicken, wird die Bearbeitungsseite **Anführungszeichen** nicht geladen. Sie können das Produkt nicht konfigurieren und Änderungen speichern. Dieses Problem tritt auch in Admin auf, wenn ein Produkt durch **SKU** zu einer Bestellung hinzugefügt oder ein Produkt durch **SKU** in **Erweiterter Checkout** (**Admin** &gt; **Customers* &gt; **Alle Kunden**&gt; **Kundenbearbeitung*&gt; **Warenkorb verwalten**). Dieses Problem wird in einem Patch für Adobe Commerce 2.4.1 behoben.
exl-id: 73f7231b-b496-4250-b9e2-29427c772d56
feature: Admin Workspace, B2B, Catalog Management, Configuration, Products, Quotes
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 B2B Admin kann kein konfigurierbares Produkt zum Anführungszeichen hinzufügen

In diesem Artikel wird über ein bekanntes Problem in Commerce Admin bei der Verwaltung eines B2B-Zitats gesprochen. Es ist nicht möglich, ein konfigurierbares Produkt von **SKU** zum Angebot hinzuzufügen. Wenn Sie auf die Schaltfläche &quot;**Zu Anführungszeichen hinzufügen**&quot;klicken, hängt das Laden der Bearbeitungsseite &quot;**Anführungszeichen**&quot;an und Sie können das Produkt nicht konfigurieren und Änderungen speichern. Dieses Problem tritt auch in Admin auf, wenn ein Produkt durch **SKU** zu einer Bestellung hinzugefügt oder ein Produkt durch **SKU** in **Erweiterter Checkout** (**Admin** > **Kunden** > **Alle Kunden** > **Kunden bearbeiten** > **Einkauf verwalten hinzugefügt wird art**). Dieses Problem wird in einem Patch für Adobe Commerce 2.4.1 behoben.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.4.0
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

## Problem

<u>Voraussetzungen</u>

* Adobe Commerce 2.4.0 ist installiert.
* B2B wird installiert.
* Setzen Sie B2B-Funktionen auf **Unternehmen aktivieren =** *Ja* , **Freigegebenen Katalog aktivieren =** *Nein* und **B2B-Angebot aktivieren =** *Ja*.
* Erstellen Sie ein Kundenkonto.
* Erstellen Sie ein Unternehmenskonto mit dem zuvor erstellten Kunden als Unternehmensadministrator.
* Erstellen Sie ein einfaches Produkt (Beispiel: Name &amp; **SKU** = TEST SIMPLE 1), das nicht **Standard (Allgemein)** zugewiesen ist.
* Bitten Sie den Unternehmensadministrator, ein Angebot mit dem oben erstellten einfachen Produkt anzufordern (Beispiel: TEST SIMPLE 1).

<u>Zu reproduzierende Schritte</u>

1. Navigieren Sie zum Commerce Admin-Bedienfeld.
1. Wechseln Sie zu **Verkauf > Anführungszeichen**.
1. Öffnen Sie das **Zitat**.
1. Klicken Sie auf die Schaltfläche **Produkt von SKU hinzufügen** .
1. Geben Sie die **SKU** eines anderen Produkts (Beispiel: TEST SIMPLE 2) in das Eingabefeld **Enter SKU** ein.
1. Geben Sie eine gültige Menge in das Eingabefeld **Menge** ein.
1. Klicken Sie auf die Schaltfläche **Zu Anführungszeichen hinzufügen** .

<u>Erwartete Ergebnisse</u>

* Das Raster **Produkte nicht zum Zitat hinzugefügt** , das den Namen und die **SKU** des erstellten Produkts enthält, wird erwartungsgemäß angezeigt.
* Nachdem das Produkt konfiguriert wurde, kann es der Administrator dem **Zitat** hinzufügen, indem er wie erwartet auf die Schaltfläche **Produkte zu Zitat hinzufügen** klickt.

<u>Tatsächliche Ergebnisse</u>

* Das Raster **Produkte, die nicht zum Raster &quot;Zitat&quot;** hinzugefügt wurden und den Namen und die **SKU** des erstellten Produkts enthalten, wird nicht angezeigt.
* Die Seite **Zitat** wird nicht mehr geladen.

## Empfehlung

Derzeit gibt es keine Problemumgehung bei der Bearbeitung von B2B-Zitaten. Für die Verwaltung von Bestellungen und Warenkorb ist es jedoch möglich, Produkte aus der **Produktliste** auszuwählen, anstatt sie über **SKU** hinzuzufügen. Ein Patch zur Lösung des Problems wird für Adobe Commerce 2.4.1 verfügbar sein, das für das 4. Quartal 2020 geplant ist.

## Verwandtes Lesen

* [Bekanntes Problem mit Adobe Commerce 2.4.0: Aktualisierung der Kundenaktivitäten nicht möglich](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Rohmeldungsdaten werden in Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Fehler bei der Auftragsanzeige](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
