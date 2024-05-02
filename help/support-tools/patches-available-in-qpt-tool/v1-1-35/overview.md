---
title: '"Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.35'''
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.35.
feature: Tools and External Services
role: Admin
exl-id: 46228690-44ce-462f-b700-1aea6fa0eeab
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.35

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.35.

QPT v1.1.35 enthält die folgenden Patches:

1. **ACSD-51899**: Behebung des Problems, bei dem die standardmäßige Versandadresse im Schritt zum Checkout-Versand automatisch mit einer zuvor ausgewählten In-Store-Abholadresse ausgefüllt wird.
1. **ACSD-52041**: Behebt das Problem, bei dem die Fehlermeldung: *[FEHLER] [!DNL Page Builder] 5 Sekunden lang gerendert wurde, ohne Sperren freizugeben*. erscheint in [!DNL Chrome] Browser beim Speichern von mit bearbeiteten Inhalten [!DNL Page Builder].
1. **ACSD-52095**: Behebt das Problem, bei dem der `manage_stock` wurde in der CSV-Datei nach dem Produktexport fälschlicherweise auf 0 gesetzt.
1. **ACSD-51358**: Behebung des Problems, bei dem das Entfernen einer geplanten Aktualisierung ohne Enddatum dazu führte, dass andere geplante Aktualisierungen für dieselbe Entität entfernt wurden.
1. **ACSD-48070**: Behebung des Problems, bei dem beim Bearbeiten einer geplanten Aktualisierung eine Ausnahme Trigger wurde.
1. **ACSD-51890**: Behebt das Problem, bei dem der [!UICONTROL Submit review] -Schaltfläche kann mehrmals ohne [!DNL Google] reCAPTCHA v3-Validierung.
1. **ACSD-51984**: Behebung des Problems, bei dem die Option deaktiviert war *Standardwert und nicht standardmäßige Produktfeldwerte verwenden* werden nicht für die zweite Website-, Store- und Store-Ansicht gespeichert.
1. **ACSD-52398**: Behebt den Fehler *Die angeforderte Menge ist nicht verfügbar* tritt auf, wenn versucht wird, die Menge eines gebündelten Produkts im Warenkorb auf der Storefront zu aktualisieren.
1. **ACSD-52786**: Behebung des Problems, bei dem eine SKU-Bedingung für Katalogregeln auf alle Produkte angewendet wird, die mit der angegebenen SKU beginnen.
1. **ACSD-52921**: Behebung des Problems, bei dem ein interner Fehler auftritt, wenn von GraphQL Warenkorbdetails angefordert werden, wenn ein konfigurierbares Produkt außerhalb des Lagerbestands im Warenkorb vorhanden ist.
1. **ACSD-51683**: Behebung des Problems, bei dem eine anpassbare Option nicht mit GraphQL zum Warenkorb hinzugefügt werden kann.
1. **ACSD-52133**: Behebung des Problems, bei dem ein Kundenkonto nach einem Upgrade nicht gespeichert werden kann.
1. **ACSD-52202**: Behebung des Problems, bei dem sich die verkaufbare Menge des Standardbestands fälschlicherweise auf 0 ändert, wenn ein nicht standardmäßiges Lager bei Bestellerfüllung auf 0 qty geändert wird.
1. **ACSD-51265**: Behebt das Problem mit `catalog_product_price` Neuindizierungsleistung bei zu vielen gebündelten Produkten im System.
1. **ACSD-52831**: Behebung des Problems, bei dem Kunden keine begebbaren Kursaufträge platzieren können, wenn [!DNL Google reCAPTCHA v3 Invisible] aktiviert ist.
1. **ACSD-51845**: Behebung des Problems, bei dem nachfolgende Produkte mit Stufenpreisen und verschiedenen Attributsätzen nicht über die asynchrone Massen-REST-API aktualisiert werden können.
1. **ACSD-52815**: Behebung des Problems, bei dem die Eingabe für das Mengenfeld einer nicht standardmäßigen Quelle nur bis zu 6 Stellen unterstützt, im Gegensatz zu 8 für ein Standardbestand.
1. **ACSD-51149**: Behebt das Problem, bei dem [!UICONTROL Scheduled ImportExport] mit aktivierten [!UICONTROL Catalog Permissions] Invalidierung von Indexern und anschließende Cache-Leerung durch Cron.
1. **ACSD-50815**: Behebung des Problems, bei dem die Dezimalzahl für ein einfaches Produkt nicht für eine neue gebündelte Produktoption verwendet werden kann.
1. **ACSD-52399**: Behebt das Problem, bei dem die konfigurierbare Produktoption mit einer verkäuflichen Menge von 0 angezeigt wird. *Auf Lager* auf der Produktseite.

Navigieren Sie über das Menü links zu einer bestimmten Patch-Seite.
