---
title: Kann ich Aktualisierungen der Inhalts-Staging-Umgebung für Preise in einem freigegebenen Katalog planen?
description: Adobe Commerce bietet nicht die Möglichkeit, eine Preisaktualisierung ([Content-Staging](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html?lang=de)) für ein oder mehrere Produkte in einem freigegebenen Katalog zu planen.
exl-id: 5482326f-54c2-4efc-8e5e-6d075ee5be55
feature: Catalog Management, Customer Service
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%
---
# Kann ich Aktualisierungen der Inhalts-Staging-Umgebung für Preise in einem freigegebenen Katalog planen?

Adobe Commerce bietet nicht die Möglichkeit, eine Preisaktualisierung ([Content-Staging](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html?lang=de)) für ein oder mehrere Produkte in einem freigegebenen Katalog zu planen.

Das bedeutet, dass Sie eine solche Preisaktualisierung nicht direkt über das Menü **Preise und Struktur festlegen** im Admin-Bedienfeld von Commerce planen können (es gibt keine Schaltfläche **Neue Aktualisierung planen** in diesem Menü).

Sie können jedoch auch alternative Methoden verwenden und eine Preisaktualisierung für Folgendes planen:

* Eine Kundengruppe
* Der Grundpreis des Produkts

## Planen der Preisaktualisierung für eine Kundengruppe

1. Starten Sie [Planung einer neuen Produktaktualisierung](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html?lang=de).
1. Scrollen Sie nach unten zum Feld **Preis** und klicken Sie auf **Erweiterte**&quot;.

   ![Advanced_Pricing.png](assets/advanced_pricing.png){width="600"}

1. Wählen Sie **Abschnitt „Kundengruppenpreis** die gewünschte Kundengruppe aus und legen Sie den aktualisierten Preis fest.

   ![customer_group_price.png](assets/customer_group_price.png){width="700"}

1. Planen Sie die Aktualisierung wie gewohnt ab.

In diesem Workflow können Sie den Preis nur für ein einzelnes Produkt aktualisieren. Eine Massenpreisaktualisierung ist nicht verfügbar.

Denken Sie daran: Freigegebene Kataloge nutzen die Kundengruppenpreise.

**Verwandte Dokumentation**

* [Planung einer Aktualisierung (Content-Staging](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html?lang=de) in unserem Benutzerhandbuch.
* [Advanced Pricing](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html?lang=de) in unserem Benutzerhandbuch.

## Planen der Preisaktualisierung für den Basispreis

Siehe den entsprechenden Artikel: [Wie wirkt sich die Grundpreisänderung auf den Preis des geteilten Katalogs aus?](/help/faq/general/base-price-change-affect-on-shared-catalog-price.md) in unserer Support-Wissensdatenbank.
