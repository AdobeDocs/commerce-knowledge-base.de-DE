---
title: 'Adobe Commerce 2.4.4: Teilrechnungen können nicht erstellt werden'
description: Dieser Artikel bietet einen Hotfix für das Problem, dass Benutzende keine Teilrechnungen erstellen können, wenn sie Apple Pay oder Google Pay über Braintree als Zahlungsmethoden verwenden.
exl-id: bf78cc07-9dc7-4eb8-bfdf-57ea5131effb
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Adobe Commerce 2.4.4: Teilrechnungen können nicht erstellt werden

Dieser Artikel bietet einen Hotfix für das Problem, dass Benutzende keine Teilrechnungen erstellen können, wenn sie Apple Pay oder Google Pay über Braintree als Zahlungsmethoden verwenden.

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

## Problem

Bei Verwendung von Apple Pay oder Google Pay als Zahlungsmethoden erhalten Benutzerinnen und Benutzer die Fehlermeldung &quot;*Der Befehl ‚vault_collection‘ existiert nicht. Überprüfen Sie den Befehl und versuchen Sie es erneut.*&quot; beim Erstellen von Teilrechnungen.

<u>Schritte zur Reproduktion</u>:

1. Öffnen Sie Ihre Adobe Commerce-Website.
1. Fügen Sie ein einfaches Produkt zum Warenkorb hinzu (Menge 2).
1. Wählen Sie **Apple Pay** oder **Google Pay** als Zahlungsmethode aus dem Warenkorb.
1. Bestellung aufgeben.
1. Öffnen Sie die Auftragsdetails über das Backend.
1. Teilrechnung erstellen.
1. Erstellen Sie eine weitere Rechnung für den Restbetrag.

<u>Erwartete Ergebnisse</u>:

Teilrechnungen werden erstellt.

<u>Tatsächliche Ergebnisse</u>:

Die erste Teilrechnung wird erstellt. Beim Erstellen der zweiten Teilrechnung wird dem Benutzer folgende Fehlermeldung angezeigt: *Der Befehl ‚vault_collection‘ existiert nicht. Überprüfen Sie den Befehl und versuchen Sie es erneut*.

## Ursache

Adobe Commerce speichert Kreditkartendetails im Tresor, um Teilrechnungen zu erstellen. Derzeit gibt es keine Funktionen, um Apple Pay und Google Pay zu tresoren.

## Lösung

Um das Problem zu beheben, führen Sie den folgenden Patch durch:

[Braintree_disabled_partial_collection_for_applepay_googlepay.zip](assets/braintree-disabled-partial-capture-for-applepay-googlepay.zip)

## Anwenden des Patches

Anweisungen [ Sie unter „Anwenden eines Composer-Patches von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).
