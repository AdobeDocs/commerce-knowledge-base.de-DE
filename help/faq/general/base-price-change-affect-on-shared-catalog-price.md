---
title: Änderung des Basispreises beeinflusst den gemeinsamen Katalogpreis
description: "Dieser Artikel beantwortet die Frage: Wenn ein Produkt in einem freigegebenen Katalog einen benutzerdefinierten Preis hat und sich der Basispreis des Produkts ändert (z. B. nach einer geplanten Aktualisierung), welcher Preis gilt im freigegebenen Katalog?"
exl-id: 916678c1-ada6-4f23-af16-b107cb83ff16
feature: Catalog Management
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# Änderung des Basispreises beeinflusst den gemeinsamen Katalogpreis

In diesem Artikel wird die Frage beantwortet: Wenn ein Produkt in einem freigegebenen Katalog einen benutzerdefinierten Preis hat und sich der Basispreis des Produkts ändert (z. B. nach einer geplanten Aktualisierung), welcher Preis gilt im freigegebenen Katalog?

## Wenn der benutzerdefinierte Preis auf Prozentsatz gesetzt ist, ändert sich auch der gemeinsame Katalogpreis

Wenn der benutzerdefinierte Preis für ein Produkt in einem freigegebenen Katalog auf &quot;Prozent&quot;festgelegt wurde, wird der freigegebene Katalogpreis des Produkts implizit aktualisiert, nachdem der Basispreis geändert wurde.

Mit anderen Worten: Wenn der Basispreis aktualisiert wird (über eine normale oder geplante Aktualisierung), ändert sich auch der freigegebene Katalogpreis nach Anwendung des Prozentsatzes.

## Wenn der benutzerdefinierte Preis auf &quot;Fest&quot;gesetzt ist, ändert sich der freigegebene Katalogpreis nicht

Wenn der benutzerdefinierte Preis für ein Produkt in einem freigegebenen Katalog auf &quot;Fest&quot;gesetzt wurde, ändert sich der Preis im freigegebenen Katalog nie - ganz gleich, wie wir den Basispreis aktualisieren (über geplante Aktualisierung, Adobe Commerce-Admin, API oder Import).

## Storefront zeigt immer den niedrigsten verfügbaren Preis an

Wenn sich der Basispreis des Produkts ändert und unter dem entsprechenden gemeinsamen Katalogpreis liegt, zeigt die Storefront den Basispreis als den niedrigsten im System verfügbaren Preis an.

## Verwandtes Lesen

[Festlegen von Preisen und Struktur für einen freigegebenen Katalog](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/define/catalog-shared-pricing-structure.html) in unserem Benutzerhandbuch.
