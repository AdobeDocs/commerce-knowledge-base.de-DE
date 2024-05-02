---
title: '"Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.39'''
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.39.
feature: Tools and External Services
role: Admin, Developer
exl-id: 48563701-0fa0-4c88-943e-78b421b806b5
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.39

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.39.

QPT v1.1.39 enthält die folgenden Patches:

1. **ACSD-53704**: Behebung des Problems, bei dem der Saldoverlauf der Bonuspunkte nach Ablauf der Bonuspunkte falsch berechnet wurde.
1. **ACSD-53583**: Verbessert die partielle Neuindizierungsleistung für *Kategorieprodukte* und *Produktkategorien* Indexer.
1. **ACSD-54026**: Behebt eine falsche Fehlermeldung für eine `updateCompanyRole` GraphQL-Anfrage an einen nicht autorisierten Benutzer.
1. **ACSD-54106**: Behebung des Problems, bei dem die Sortierung von Kategorieprodukten nach Namen für türkische Akzentzeichen falsch ist.
1. **ACSD-52219**: Behebung des Problems, bei dem gespeicherte Filter vom Admin-Raster beim häufigen Wechseln zwischen Lesezeichenansichten nicht erwartungsgemäß funktionierten.
1. **ACSD-54342**: Behebt eine falsche Fehlermeldung *Fehler in der Datenstruktur: Werte werden gemischt* wenn eine CSV-Datei ohne gültige Daten importiert wird.
1. **ACSD-54660**: Es wurde ein neues Eingabeattribut hinzugefügt. *sort* Sortieren von Kundenbestellungen in GraphQL nach `sort_field` und `sort_direction`.
1. **ACSD-54776**: Behebung des Problems, bei dem die Option deaktiviert war *[!UICONTROL Use Default Value]* und nicht standardmäßige Produktfeldwerte werden nicht für die zweite Website-, Store- und Store-Ansicht gespeichert.
1. **ACSD-53998**: Behebt das Problem, bei dem ein **[!UICONTROL Dynamic Block]** auf der Grundlage einer **[!UICONTROL Customer Segment]** funktioniert nicht ordnungsgemäß, nachdem sich ein Kundenkonto abgemeldet hat.
1. **ACSD-53204**: Fehlerbehebungen *Das Produkt kann nicht gespeichert werden.* Fehler bei gleichzeitigen Anfragen zum Hinzufügen von Bildern zur Produktgalerie mithilfe der `rest/V1/products/<sku>/media` -Endpunkt.
1. **ACSD-47657**: Es wurde ein Caching-Mechanismus für AWS-Anmeldeinformationen hinzugefügt. Ein Berechtigungsanbieter verwendet jetzt den Magento-Cache, um von AWS für die EC2-Konfiguration abgerufene Anmeldeinformationen zwischenzuspeichern.

Navigieren Sie über das Menü links zu einer bestimmten Patch-Seite.
