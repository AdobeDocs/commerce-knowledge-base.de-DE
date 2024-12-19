---
title: 'Bekanntes Problem in Adobe Commerce 2.4.0: Fehler bei der Anzeige von Bestellungen'
description: 'Dieser Artikel bietet eine Problemumgehung für ein bekanntes Problem in Adobe Commerce bei einem Fehler bei der Anzeige von Bestellungen. Wenn angemeldete Kunden ihre Bestellungen im Menü **Mein Konto** überprüfen (**Mein Konto &gt; Meine Bestellungen**), kann im Bestellraster von Seite 2 aus die Anzahl der Bestellungen pro Seite nicht auf 20 umgeschaltet werden, wenn elf Bestellungen vorhanden sind. Wenn außerdem mehr Bestellungen vorhanden sind als pro Seite angezeigt werden, wird beim Navigieren zur letzten Seite mit Bestellungen, die Änderung der Anzahl der pro Seite angezeigten Bestellungen zu der Fehlermeldung: *Sie haben keine Bestellungen aufgegeben*. Dieses Problem wird mit Adobe Commerce 2.4.1 behoben.'
exl-id: a6d300e1-1cbc-42b9-997d-d72f8765517b
feature: B2B, Categories, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# Bekanntes Problem in Adobe Commerce 2.4.0: Fehler bei der Anzeige von Bestellungen

Dieser Artikel bietet eine Problemumgehung für ein bekanntes Problem in Adobe Commerce bei einem Fehler bei der Anzeige von Bestellungen. Wenn angemeldete Kunden ihre Bestellungen im Menü **Mein Konto** überprüfen (**Mein Konto > Meine Bestellungen**), kann im Bestellraster von Seite 2 aus die Anzahl der Bestellungen pro Seite nicht auf 20 umgeschaltet werden, wenn elf Bestellungen vorhanden sind. Wenn außerdem mehr Bestellungen pro Seite angezeigt werden, als für die Anzeige pro Seite konfiguriert sind, wird beim Navigieren zur letzten Seite mit Bestellungen, die Änderung der Anzahl der pro Seite angezeigten Bestellungen zu der folgenden Fehlermeldung geführt: *Sie haben keine Bestellungen aufgegeben*. Dieses Problem wird mit Adobe Commerce 2.4.1 behoben.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.4.0
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

## Problem

<u>Voraussetzungen</u>

* Adobe Commerce 2.4.0 ist installiert.
* Erstellen Sie mindestens eine Kategorie und ein einfaches Produkt.

<u>Schritte zur Reproduktion</u>

1. Erstellen Sie 11 Bestellungen mit Produkten.
1. Gehen Sie zu **Mein Konto**.
1. Gehen Sie zu **Meine Bestellungen**.
1. Klicken Sie auf die zweite Seite, um die 11. Reihenfolge im Auftragsraster anzuzeigen.
1. Wählen **Anzeigen = 20 pro Seite** aus dem Dropdown-Menü aus.

<u>Erwartetes Ergebnis</u>

Alle 11 Bestellungen werden wie erwartet auf der ersten Seite angezeigt.

<u>Tatsächliches Ergebnis</u>

Die *Sie haben keine Bestellungen aufgegeben* wird angezeigt.

## Abhilfe

Die Problemumgehung besteht darin, den Käufer die Seite **Meine Bestellungen** erneut öffnen zu lassen, und dann wird die Liste der Bestellungen korrekt angezeigt. Das Problem wird in der nächsten Version, Adobe Commerce 2.4.1, behoben, die im 4. Quartal 2020 veröffentlicht werden soll.

## Verwandte Lesungen in unserer Support-Wissensdatenbank

* [Bekanntes Problem in Adobe Commerce 2.4.0 - Aktualisierung der Aktivitäten des Kunden funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Rohnachrichtendaten werden in der Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B-Admin kann kein konfigurierbares Produkt zum Angebot hinzufügen](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
