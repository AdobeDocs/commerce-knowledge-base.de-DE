---
title: '"Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.31'''
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.31.
exl-id: 0d93619e-0ae6-4dba-9b76-8aeb026c456d
feature: Tools and External Services
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.31

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.31.

QPT v1.1.31 umfasst die folgenden Patches:

1. **ACSD-50817**: Optimiert den Cron-Auftrag `sales_clean_quotes` schnellere Ausführung durch Hinzufügen eines zusammengesetzten Index auf `store_id` und `updated_at` Spalten in der Anführungszeichentabelle.
1. **ACSD-50345**: Behebt das Problem, bei dem: [!DNL Google reCAPTCHA v2] nach Übermittlung einer fehlgeschlagenen Zahlung nicht neu geladen wird, [!DNL Google reCAPTCHA v3 Invisible] funktioniert nicht beim Checkout und die Bestellung kann nicht platziert werden und [!UICONTROL PlaceOrder] -Ereignis nicht ausgelöst wurde.
1. **ACSD-49392**: Behebung des Problems, bei dem der Auftragsstatus nach einer teilweisen Rückerstattung für ein gebündeltes Produkt zu &quot;geschlossen&quot;geändert wurde.
1. **ACSD-51036**: Behebung des Problems, bei dem die Wettlaufsituationen bei gleichzeitigen REST-API-Aufrufen zu einem Überschreiben der Versandstatusinformationen in der [!UICONTROL Items Ordered] Tabelle.
1. **ACSD-50858**: Behebung des Problems, bei dem ein Gutschein fälschlicherweise als nach einer fehlgeschlagenen Kartenzahlung als verwendet markiert wurde.

Navigieren Sie über das Menü links zu einer bestimmten Patch-Seite.
