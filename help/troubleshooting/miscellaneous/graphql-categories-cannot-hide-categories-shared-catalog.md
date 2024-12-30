---
title: GraphQL-Abfrage zum Ausblenden von Kategorien funktioniert nicht mit dem freigegebenen B2B-Katalog
description: Dieser Artikel bietet eine Lösung für den Fall, dass die Funktion „Freigegebener B2B-Katalog“ nicht mit der Abfrage von GraphQL-Kategorien funktioniert, um Kategorien auszublenden.
exl-id: bdafa8d9-b637-409e-86b5-d132bccfe0b8
feature: B2B, Catalog Management, Categories, GraphQL, Customer Service
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# GraphQL-Abfrage zum Ausblenden von Kategorien funktioniert nicht mit dem freigegebenen B2B-Katalog


## Betroffene Produkte und Versionen

* Adobe Commerce on Cloud Infrastructure und Adobe Commerce On-Premises 2.4.3

## Problem

GraphQL-Kategorien und `categoryList`-Abfragen ignorieren die Kategorieberechtigung, um Kategorien in einem freigegebenen Katalog auszublenden. Dies geschieht bei allen Händlern mit aktivierter Funktion „B2B-freigegebener Katalog“ auf Adobe Commerce 2.4.3.

<u>Schritte zur Reproduktion</u>:

Voraussetzungen:

Dies geschieht bei allen Händlern mit Adobe Commerce 2.4.3, bei denen die PWA-Storefront die GraphQL-API mit aktivierter Funktion „B2B Shared Catalog“ und Adobe Commerce Backend/Admin nutzt.

1. Erstellen Sie mehrere Kategorien (CAT1,CAT2).
1. Erstellen Sie einen privaten freigegebenen Katalog.
1. Erstellen Sie einen Unternehmensbenutzer und weisen Sie ihn dem oben genannten freigegebenen Katalog zu.
1. Weisen Sie jeder dieser Kategorien einige Produkte zu.
1. Weisen Sie CAT1 dem benutzerdefinierten Katalog zu und heben Sie die Zuweisung von CAT2 zum benutzerdefinierten privaten Katalog auf. Dadurch wird die Zuweisung aller Produkte aus CAT2 im freigegebenen Katalog aufgehoben.
1. Speichern Sie den benutzerdefinierten Katalog.
1. Legen Sie die Kategorieberechtigung für die Kategorie CAT2 auf *Ablehnen* fest und legen Sie die Kundengruppe auf den obigen privaten Katalog fest.
1. Führen Sie die Abfrage `categoryList query` oder Kategorien als Unternehmensbenutzer aus Schritt 3 aus.

<u>Erwartete Ergebnisse</u>:

In den Ergebnissen wird nur CAT1 angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Alle Kategorien werden angezeigt, unabhängig davon, ob sie im freigegebenen Katalog zugewiesen/nicht zugewiesen sind oder welche Kategorieberechtigungen es gibt.

## Ursache

Die Funktion wurde nicht implementiert.

## Lösung

Das Problem wird im Rahmen der Version 2.4.4 behoben, und Händler sollten [ein Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) um einen benutzerdefinierten Patch zu erhalten, wenn sie eine Lösung vor der Version 2.4.4 benötigen.

## Verwandtes Lesen

* [Best Practice Adobe Commerce Anzahl der ](https://support.magento.com/hc/en-us/articles/360048176832) in unserer Support-Wissensdatenbank.
