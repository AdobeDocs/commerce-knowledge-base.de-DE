---
title: Einfluss der Basispreisänderung auf den Preis des freigegebenen Katalogs
description: 'Dieser Artikel beantwortet die Frage: Wenn ein Produkt in einem freigegebenen Katalog einen benutzerdefinierten Preis hat und sich der Grundpreis des Produkts ändert (z. B. nach einer geplanten Aktualisierung), welcher Preis gilt dann im freigegebenen Katalog?'
exl-id: 916678c1-ada6-4f23-af16-b107cb83ff16
feature: Catalog Management
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# Einfluss der Basispreisänderung auf den Preis des freigegebenen Katalogs

Dieser Artikel beantwortet die Frage: Wenn ein Produkt in einem freigegebenen Katalog einen benutzerdefinierten Preis hat und sich der Grundpreis des Produkts ändert (z. B. nach einer geplanten Aktualisierung), welcher Preis gilt dann im freigegebenen Katalog?

## Wenn der benutzerdefinierte Preis auf „Prozentsatz“ gesetzt ist, ändert sich auch der Preis des freigegebenen Katalogs

Wenn der benutzerdefinierte Preis für ein Produkt in einem freigegebenen Katalog auf Prozent festgelegt wurde, wird der Preis für den freigegebenen Katalog des Produkts implizit aktualisiert, nachdem der Grundpreis geändert wurde.

Mit anderen Worten, wenn der Basispreis aktualisiert wird (über eine normale oder geplante Aktualisierung), ändert sich der Preis des geteilten Katalogs auch nach Anwendung des prozentualen Rabatts.

## Wenn der benutzerdefinierte Preis auf „Fester, freigegebener Katalogpreis“ gesetzt ist, ändert sich dieser nicht

Wenn der benutzerdefinierte Preis für ein Produkt in einem freigegebenen Katalog auf Festgelegt festgelegt wurde, ändert sich der Preis im freigegebenen Katalog nie - unabhängig davon, wie wir den Grundpreis aktualisieren (über geplante Aktualisierung, Adobe Commerce Admin, API oder Import).

## Die Storefront zeigt immer den niedrigsten verfügbaren Preis an

Wenn sich der Grundpreis des Produkts ändert und niedriger als der entsprechende freigegebene Katalogpreis wird, zeigt die Storefront den Grundpreis als niedrigsten im System verfügbaren Preis an.

## Verwandtes Lesen

[Festlegen von Preisen und Strukturen für einen freigegebenen ](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/define/catalog-shared-pricing-structure.html?lang=de)) in unserem Benutzerhandbuch.
