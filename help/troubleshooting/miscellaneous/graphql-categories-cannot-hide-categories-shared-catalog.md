---
title: GraphQL-Abfrage zum Ausblenden von Kategorien, die nicht mit einem freigegebenen B2B-Katalog funktionieren
description: Dieser Artikel bietet eine Lösung für den Fall, dass die Funktion eines freigegebenen B2B-Katalogs nicht mit der GraphQL-Kategorieabfrage funktioniert, um Kategorien auszublenden.
exl-id: bdafa8d9-b637-409e-86b5-d132bccfe0b8
feature: B2B, Catalog Management, Categories, GraphQL, Customer Service
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# GraphQL-Abfrage zum Ausblenden von Kategorien, die nicht mit einem freigegebenen B2B-Katalog funktionieren


## Betroffene Produkte und Versionen

* Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.4.3

## Problem

GraphQL-Kategorien und `categoryList` -Abfragen ignorieren die Kategorieberechtigung zum Ausblenden von Kategorien in einem freigegebenen Katalog. Dies geschieht bei allen Händlern in Adobe Commerce 2.4.3, bei denen die Funktion für freigegebenen B2B-Katalog aktiviert ist.

<u>Zu reproduzierende Schritte</u>:

Voraussetzungen:

Dies geschieht bei allen Händlern in Adobe Commerce 2.4.3 mit PWA-Storefront, die die GraphQL-API mit Adobe Commerce-Backend/Admin nutzen, bei der die Funktion &quot;B2B Shared Catalog&quot;aktiviert ist.

1. Erstellen Sie mehrere Kategorien (CAT1, CAT2).
1. Erstellen Sie einen privaten freigegebenen Katalog.
1. Erstellen Sie einen Unternehmensbenutzer und weisen Sie ihn dem oben freigegebenen Katalog zu.
1. Weisen Sie jeder dieser Kategorien einige Produkte zu.
1. Weisen Sie dem benutzerdefinierten Katalog CAT1 zu und heben Sie die Zuweisung von CAT2 aus dem benutzerdefinierten privaten Katalog auf. Dadurch wird die Zuweisung aller Produkte von CAT2 aus dem freigegebenen Katalog aufgehoben.
1. Speichern Sie den benutzerdefinierten Katalog.
1. Legen Sie die Kategorieberechtigung für CAT2 auf *Ablehnen* Kategorie durchsuchen und die Kundengruppe auf den oben genannten privaten Katalog setzen.
1. Führen Sie die `categoryList query` oder der Kategorienabfrage als Unternehmensbenutzer aus Schritt 3.

<u>Erwartete Ergebnisse</u>:

Nur die CAT1 wird in den Ergebnissen angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Alle Kategorien werden unabhängig davon angezeigt, ob sie im freigegebenen Katalog zugewiesen/nicht zugewiesen wurden oder welche Kategorieberechtigungen gewährt wurden.

## Ursache

Die Funktionalität wurde nicht implementiert.

## Lösung

Das Problem wird in Version 2.4.4 behoben, und Händler sollten [Einreichen eines Tickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) um einen benutzerspezifischen Patch zu erhalten, wenn sie vor Version 2.4.4 eine Lösung benötigen.

## Verwandtes Lesen

* [Best Practice Adobe Commerce-Kategorienbeschränkungen](https://support.magento.com/hc/en-us/articles/360048176832) in unserer Wissensdatenbank.
