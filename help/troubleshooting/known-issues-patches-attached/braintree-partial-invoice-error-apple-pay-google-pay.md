---
title: 'Adobe Commerce 2.4.4: Teilrechnungen können nicht erstellt werden'
description: Dieser Artikel enthält einen Hotfix für das Problem, bei dem Benutzer keine Teilrechnungen erstellen können, wenn sie Apple Pay oder Google Pay Through Braintree als Zahlungsmethoden verwenden.
exl-id: bf78cc07-9dc7-4eb8-bfdf-57ea5131effb
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Adobe Commerce 2.4.4: Teilrechnungen können nicht erstellt werden

Dieser Artikel enthält einen Hotfix für das Problem, bei dem Benutzer keine Teilrechnungen erstellen können, wenn sie Apple Pay oder Google Pay Through Braintree als Zahlungsmethoden verwenden.

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

## Problem

Bei Verwendung von Apple Pay oder Google Pay als Zahlungsmethoden erhalten Benutzer den Fehler &quot;*Der Befehl &quot;vault_Capture&quot;ist nicht vorhanden. Überprüfen Sie den Befehl und versuchen Sie es erneut.*&quot; beim Erstellen von Teilrechnungen.

<u>Zu reproduzierende Schritte</u>:

1. Öffnen Sie Ihre Adobe Commerce-Website.
1. Fügen Sie ein einfaches Produkt zum Warenkorb hinzu (2. Quartal).
1. Wählen Sie **Apple Pay** oder **Google Pay** als Zahlungsmethode aus dem Warenkorb.
1. Platzieren Sie die Bestellung.
1. Öffnen Sie Bestelldetails über das Back-End.
1. Erstellen Sie eine Teilrechnung.
1. Erstellen Sie eine weitere Rechnung für den verbleibenden Betrag.

<u>Erwartete Ergebnisse</u>:

Teilrechnungen werden erstellt.

<u>Tatsächliche Ergebnisse</u>:

Die erste Teilrechnung wird erstellt. Beim Erstellen der zweiten partiellen Rechnung erhalten Benutzer den folgenden Fehler: *Der Befehl &quot;vault_collection&quot;ist nicht vorhanden. Überprüfen Sie den Befehl und versuchen Sie es erneut*.

## Ursache

Adobe Commerce speichert Kreditkartendetails im Tresor, um Teilrechnungen zu erstellen. Derzeit gibt es keine Funktionalität, um Apple Pay und Google Pay zu überprüfen.

## Lösung

Um das Problem zu beheben, wenden Sie den folgenden Patch an:

[Braintree_disabled_partielle_Capture_for_applepay_googlepay.zip](assets/braintree-disabled-partial-capture-for-applepay-googlepay.zip)

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches.
