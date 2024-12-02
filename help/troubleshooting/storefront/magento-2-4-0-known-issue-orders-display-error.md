---
title: 'Bekanntes Problem mit Adobe Commerce 2.4.0: Bestellungen zeigen Fehler an'
description: 'Dieser Artikel bietet eine Behelfslösung für ein bekanntes Problem in Adobe Commerce bei einem Auftragsanzeigefehler. Wenn angemeldete Kunden ihre Bestellungen im Menü **Mein Konto** (**Mein Konto &gt; Meine Bestellungen**) überprüfen, kann das Bestellraster die Anzahl der Bestellungen pro Seite nicht von Seite 2 auf 20 umstellen, wenn 11 Bestellungen vorhanden sind. Wenn beim Navigieren zur letzten Seite mit Bestellungen mehr Bestellungen vorhanden sind, als für die Anzeige pro Seite konfiguriert ist, erzeugt die Änderung der Anzahl der pro Seite angezeigten Bestellungen die Fehlermeldung: *Sie haben keine Bestellungen aufgegeben*. Dieses Problem wird in Adobe Commerce 2.4.1 behoben.'
exl-id: a6d300e1-1cbc-42b9-997d-d72f8765517b
feature: B2B, Categories, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# Bekanntes Problem mit Adobe Commerce 2.4.0: Bestellungen zeigen Fehler an

Dieser Artikel bietet eine Behelfslösung für ein bekanntes Problem in Adobe Commerce bei einem Auftragsanzeigefehler. Wenn angemeldete Kunden ihre Bestellungen im Menü **Mein Konto** (**Mein Konto > Meine Bestellungen**) überprüfen, kann die Anzahl der Bestellungen pro Seite von Seite 2 bei 11 Bestellungen nicht auf 20 umgestellt werden. Wenn beim Navigieren zur letzten Seite mit Bestellungen mehr Bestellungen vorhanden sind, als für die Anzeige pro Seite konfiguriert ist, erzeugt eine Änderung der Anzahl der pro Seite angezeigten Bestellungen die Fehlermeldung: *Sie haben keine Bestellungen aufgegeben*. Dieses Problem wird in Adobe Commerce 2.4.1 behoben.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.4.0
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

## Problem

<u>Voraussetzungen</u>

* Adobe Commerce 2.4.0 ist installiert.
* Erstellen Sie mindestens eine Kategorie und ein einfaches Produkt.

<u>Zu reproduzierende Schritte</u>

1. Erstellen Sie 11 Bestellungen mit Produkten.
1. Wechseln Sie zu **Mein Konto**.
1. Wechseln Sie zu **Meine Bestellungen**.
1. Klicken Sie auf die zweite Seite, um die 11. Bestellung im Bestellraster anzuzeigen.
1. Wählen Sie **Anzeigen = 20 pro Seite** aus dem Dropdown-Menü aus.

<u>Erwartetes Ergebnis</u>

Alle 11 Bestellungen werden wie erwartet auf der ersten Seite angezeigt.

<u>Tatsächliches Ergebnis</u>

Die Fehlermeldung *Sie haben keine Bestellungen aufgegeben* wird angezeigt.

## Workaround

Um dieses Problem zu umgehen, muss der Käufer die Seite **Meine Bestellungen** erneut öffnen. Anschließend wird die Liste der Bestellungen korrekt angezeigt. Das Problem wird in der nächsten Version, Adobe Commerce 2.4.1, behoben, die für das 4. Quartal 2020 geplant ist.

## Verwandte Lesungen in unserer Wissensdatenbank

* [Bekanntes Problem mit Adobe Commerce 2.4.0 - Aktualisierung der Kundenaktivitäten funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Rohmeldungsdaten werden in Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B Admin kann kein konfigurierbares Produkt zum Anführungszeichen hinzufügen](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
