---
title: '"Übersicht: [!DNL Quality Patches Tool] (QPT) v1.0.7'''
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.0.7.
exl-id: 2415ca7a-4aec-4a63-9ae9-ee7b29bbc8d7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.7 - Übersicht

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.0.7.

QPT v1.0.7 enthält die folgenden Patches:

1. **MDVA-29148**: Behebt das Problem beim Erstellen eines Produkts über einen API-Aufruf, das benutzerdefinierte Produktattribut von `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (wie Multiselect) verwendet seinen Standardwert nicht, wenn in der Payload kein Wert angegeben wurde.
1. **MDVA-29389**: Behebung des Problems mit der erweiterten Berichterstellung, bei dem die Variable `analytics_collect_data` cronjob sagt: *Der Port muss innerhalb des Host-Parameters konfiguriert werden (z. B. localhost:3306).*.
1. **MDVA-30594**: Behebung des Problems, bei dem eine Bestellung mit mehreren Adressen beim Checkout nicht gespeichert werden konnte, wenn FPT konfiguriert wurde.
1. **MDVA-30782**: Behebung des Problems, bei dem der dynamische Block unabhängig von der Warenkorbregel angezeigt wird.
1. **MDVA-30815**: Behebung des Problems, bei dem geändert wird, wie viele Suchergebnisse auf der Suchergebnisseite angezeigt werden sollen.
1. **MDVA-30837**: Fügt Konfigurationsoptionen für die Berechnung des kostenlosen Versands hinzu, damit der Benutzer den Mindestbestellbetrag so konfigurieren kann, dass der kostenlose Versand auf der Grundlage der Zwischensumme (oder Gesamtsumme) erfolgt.
1. **MDVA-30945**: Behebung des Problems, bei dem Sie beim Aktualisieren von Warenkorb eine Fehlermeldung mit fatalen Folgen erhalten `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.
1. **MDVA-30972**: Behebung des Problems, bei dem der benutzerdefinierte Bestellstatus in geändert wurde. *Verarbeitung* nach Teillieferung mit WebAPI.
1. **MDVA-31007**: Behebung des Problems, bei dem benutzerdefinierte Adressattribute auf der Seite mit den Bestelldetails in meinem Kontobereich und im Backend nicht korrekt angezeigt werden.
1. **MDVA-31021**: Behebt das Problem, bei dem Leistungsprobleme in `module-catalog-import-export/Model/Import/Product/Option.php`. Wenn mehr als ~100.000 Datensätze in `catalog_product_option` -Tabelle verwenden, dauert die Validierung einer neuen CSV mit einem einzelnen Produkt weniger als 10 Sekunden.
1. **MDVA-31224**: Verbessert die Leistung der `catalog_product_price` Neuindizierungsvorgang für Paket-Produkte.
1. **MDVA-31282**: Behebung des Problems, bei dem doppelte Berechtigungen in [!DNL Paypal PayFlow Pro] in Adobe Commerce. Die doppelten Genehmigungen bewirken auch, dass [!DNL PayFlow Pro's] Betrugsfilter und Verdopplung der Transaktionsgebühren.
1. **MDVA-31343**: Behebt das Problem mit der entfernten Textklasse `page-layout-category-full-width` wenn eine Kategorie geplant ist.

Navigieren Sie über das Menü links zu einer bestimmten Patch-Seite.
