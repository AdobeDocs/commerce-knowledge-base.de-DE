---
title: "Übersicht: [!DNL Quality Patches Tool] (QPT) v1.0.7"
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool]  (QPT) v1.0.7 verfügbaren Patches behoben wurden.
exl-id: 2415ca7a-4aec-4a63-9ae9-ee7b29bbc8d7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Überblick über [!DNL Quality Patches Tool] (QPT) v1.0.7

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.0.7 verfügbaren Patches behoben wurden.

QPT v1.0.7 enthält die folgenden Patches:

1. **MDVA-29148**: Behebung des Problems beim Erstellen eines Produkts über einen API-Aufruf. Das benutzerdefinierte Produktattribut vom Typ `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (wie Multiselect) verwendet seinen Standardwert nicht, wenn in der Payload kein Wert angegeben wurde.
1. **MDVA-29389**: Behebung des Problems mit der erweiterten Berichterstellung, bei dem der `analytics_collect_data`-Cronjob besagt: *Port muss innerhalb des Host-Parameters konfiguriert werden (z. B. localhost:3306)*.
1. **MDVA-30594**: Behebung des Problems, bei dem eine Bestellung mit mehreren Adressen beim Checkout nicht gespeichert werden konnte, wenn FPT konfiguriert wurde.
1. **MDVA-30782**: Behebung des Problems, bei dem der dynamische Block unabhängig von der Warenkorbregel angezeigt wird.
1. **MDVA-30815**: Behebung des Problems, bei dem geändert wurde, wie viele Suchergebnisse auf der Suchergebnisseite angezeigt werden sollen.
1. **MDVA-30837**: Fügt Konfigurationsoptionen für die Berechnung des kostenlosen Versands hinzu, damit der Benutzer den Mindestbestellbetrag so konfigurieren kann, dass der kostenlose Versand auf der Grundlage der Zwischensumme (oder Gesamtsumme) erfolgt.
1. **MDVA-30945**: Behebung des Problems, bei dem Sie eine schwerwiegende Fehlermeldung erhalten, wenn Sie den Warenkorb `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php` aktualisieren.
1. **MDVA-30972**: Behebung des Problems, bei dem der benutzerdefinierte Bestellstatus nach der Erstellung eines Teilversands mit WebAPI in *Verarbeitung* geändert wurde.
1. **MDVA-31007**: Behebung des Problems, bei dem benutzerdefinierte Adressattribute auf der Seite mit Bestelldetails in meinem Kontobereich und im Backend nicht korrekt angezeigt werden.
1. **MDVA-31021**: Behebt das Problem, bei dem Leistungsprobleme in `module-catalog-import-export/Model/Import/Product/Option.php` vorliegen. Wenn die Tabelle `catalog_product_option` mehr als etwa 100.000 Datensätze enthält, dauert die Validierung einer neuen CSV mit einem einzelnen Produkt weniger als 10 Sekunden.
1. **MDVA-31224**: Verbessert die Leistung des Neuindizierungsvorgangs von `catalog_product_price` für Bundle-Produkte.
1. **MDVA-31282**: Behebung des Problems, bei dem in Adobe Commerce unter [!DNL Paypal PayFlow Pro] doppelte Berechtigungen erteilt wurden. Die doppelten Genehmigungen führen auch dazu, dass [!DNL PayFlow Pro's]-Betrugsfilter umgangen und die Transaktionsgebühren verdoppelt werden.
1. **MDVA-31343**: Behebt das Problem mit der entfernten Textklasse `page-layout-category-full-width`, wenn eine Kategorie geplant ist.

Navigieren Sie über das Menü links zu einer bestimmten Patch-Seite.
