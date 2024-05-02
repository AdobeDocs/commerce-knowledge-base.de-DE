---
title: '"Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.48'''
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.48.
feature: Tools and External Services
role: Admin, Developer
exl-id: 6170c616-312c-4de3-98dc-e2c27c376608
source-git-commit: 42712af2ce4337cd64b8dea555139e4252fb91cf
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.48

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.48.

QPT v1.1.48 enthält die folgenden Patches:

1. **ACSD-55566**: Behebt das Problem, bei dem der *[!UICONTROL mergeCart mutation]* schlägt mit einer *Interner Server-Fehler* in der GraphQL-Antwort beim Zusammenführen von Quell- und Zielcarts haben dieselben gebündelten Elemente.
1. **ACSD-56546**: Behebung des Problems, bei dem konfigurierbare und gebündelte Produkte als *[!UICONTROL Out of Stock]* auf der Storefront, wenn die *[!UICONTROL Display Out of Stock Product]* -Konfiguration deaktiviert ist.
1. **ACSD-56635**: Behebung des Problems, bei dem der importierte Kunde mit derselben E-Mail-Adresse dupliziert wird, wenn der Import mit [!UICONTROL Account Sharing] auf *[!UICONTROL Global]*.
1. **ACSD-56741**: Behebt die Fehlermeldung *Versuch, auf den Array-Versatz für den Wert des Typs null zuzugreifen* , das während `setup:upgrade` wenn die Datenbank einen benutzerdefinierten MySQL-Trigger enthält, der nicht mit dem Indexierungsmechanismus in Zusammenhang steht, und [!DNL MView].
1. **ACSD-57315**: Behebung des Problems, bei dem eine neue Transaktion in erstellt wurde. [!DNL PayPal Payflow Pro] jedes Mal **[!UICONTROL Fetch]** auf den Bildschirm &quot;Transaktion anzeigen&quot;im [!UICONTROL Admin].
1. **ACSD-57337**: Behebung des Problems, bei dem ein Admin-Benutzer mit Zugriffsbeschränkungen auf bestimmte Websites Unternehmen von allen Websites in der *[!UICONTROL Companies]* Gitter.
1. **ACSD-57394**: Behebt eine falsche Produktsortierung nach mehreren Sortierungsfeldern in GraphQL.
1. **ACSD-57565**: Behebt das Problem, bei dem der *[!UICONTROL Order]* -Dashboard zeigt fehlerhafte Bestellinformationen an, bis der Zeitraum aktualisiert wurde. Das Dashboard zeigt nun beim ersten Laden die richtigen Bestellstatistiken an.
1. **ACSD-57854**: Behebung des Problems, bei dem Produkt-GraphQL-Anforderungen deaktivierte Kategorien in den Kategorieaggregationen zurückgeben.
1. **ACSD-58008**: Behebung des Problems, bei dem beim Aktualisieren einer geplanten Aktualisierung die vorherige Version des gestaffelten Elements entfernt wird, wenn kein Enddatum angegeben ist.

Navigieren Sie über das Menü links zu einer bestimmten Patch-Seite.

