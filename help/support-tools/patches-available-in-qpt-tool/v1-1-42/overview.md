---
title: '"Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.42'''
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.42.
feature: Tools and External Services
role: Admin, Developer
exl-id: 49f7ebd6-7a5f-49da-8fac-c3c2b73b52c1
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.42

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.42.

QPT v1.1.42 umfasst die folgenden Patches:

1. **ACSD-53658**: Behebt das Problem, bei dem *[!UICONTROL Recently Viewed]* Produktdaten werden in der Store-Ansicht nicht ordnungsgemäß aktualisiert.
1. **ACSD-54626**: Behebung des Problems, bei dem Sie keine neue Bestellregel erstellen können (`createPurchaseOrderApprovalRule`) durch die `NUMBER_OF_SKUS` -Attribut über GraphQL.
1. **ACSD-53845**: Behebt das Problem mit dem MySQL-Verbindungs-Timeout beim `consumer max_messages` = 0.
1. **ACSD-54890**: Behebt das Problem, bei dem `aggregate_sales_report_bestsellers_data` verursacht MySQL-Fehler aufgrund von `/tmp` Speicherplatz vergeudet.
1. **ACSD-55112**: Behebt das Problem, bei dem der *[!UICONTROL Submit review]* -Schaltfläche kann mehrmals ohne [!DNL Google reCAPTCHA v3] Validierung.
1. **ACSD-54264**: Behebt das Problem, bei dem die Fehlermeldung *Das angeforderte Attribut kann nicht aktualisiert werden. Zeilen-ID: store_id* angezeigt, wenn ein Kunde versucht, mit einem verhandelbaren Angebot aus einer anderen Store-Ansicht auszuchecken.
1. **ACSD-54418**: Behebung des Problems, bei dem ein fester Rabatt fälschlicherweise auf jedes untergeordnete Produkt des dynamisch priorisierten Bundles angewendet wird.
1. **ACSD-55238**: Behebung des Problems beim Speichern der leeren Produktmeta-Beschreibung.
1. **ACSD-54966**: Behebung des Problems, bei dem ein Gutscheincode mit begrenzter Nutzung pro Kunde nicht wiederverwendet werden kann, wenn die vorherige Bestellung fehlgeschlagen ist.
1. **ACSD-54060**: Behebung des Problems, bei dem ein eingeschränkter Administrator ein Produkt nicht speichern kann, wenn es ein untergeordnetes Element eines anderen Produkts ist, das einem anderen Bereich zugewiesen ist.
1. **ACSD-48910**: Behebung des Problems, bei dem ein gebündeltes Produkt, das mehreren Quellen zugewiesen wurde, nach der Fakturierung und dem Versand einer Bestellung nicht mehr vorrätig ist, selbst wenn die Menge nicht null ist.
1. **ACSD-55381**: Behebt einen internen Server-Fehler bei der Abfrage `configurable_product_option_uid` und `configurable_product_option_value_uid` Felder aus B2B *[!UICONTROL Requisition list]* über GraphQL.
1. **ACSD-55628**: Fehlerkorrektur - das Hochladen einer Datei im Registrierungsformular für das Unternehmen und das Ersetzen einer Datei für ein Kundenattribut in der Storefront werden korrigiert.

Navigieren Sie über das Menü links zu einer bestimmten Patch-Seite.
