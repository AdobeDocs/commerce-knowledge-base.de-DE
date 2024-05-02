---
title: Kann ich Aktualisierungen des Content Staging für Preise in einem freigegebenen Katalog planen?
description: Adobe Commerce bietet nicht die Möglichkeit, eine Preisaktualisierung ([Content Staging](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html)) für ein oder mehrere Produkte in einem freigegebenen Katalog zu planen.
exl-id: 5482326f-54c2-4efc-8e5e-6d075ee5be55
feature: Catalog Management, Customer Service
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Kann ich Aktualisierungen des Content Staging für Preise in einem freigegebenen Katalog planen?

Adobe Commerce bietet nicht die Möglichkeit, ein Preisupdate zu planen ([Inhaltstaging](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html)) für ein oder mehrere Produkte in einem freigegebenen Katalog.

Das bedeutet, dass Sie eine solche Preisaktualisierung nicht direkt über die **Festlegen von Preisen und Struktur** Menü des Commerce Admin-Bedienfelds (es gibt keine **Neue Aktualisierung planen** in diesem Menü).

Sie können jedoch alternative Methoden verwenden und eine Preisaktualisierung für Folgendes planen:

* eine Kundengruppe
* der Basispreis des Erzeugnisses

## Preisaktualisierung für eine Kundengruppe planen

1. Starten [Planung neuer Produktaktualisierungen](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html).
1. Scrollen Sie nach unten zum **Preis** Feld und klicken Sie auf **Erweiterte Preise**.

   ![advanced_price.png](assets/advanced_pricing.png){width="600"}

1. Im **Bereich &quot;Kundengruppenpreis&quot;**, wählen Sie die gewünschte Kundengruppe aus und legen Sie den aktualisierten Preis fest.

   ![customer_group_price.png](assets/customer_group_price.png){width="700"}

1. Beenden Sie die Planung der Aktualisierung wie gewohnt.

In diesem Workflow können Sie nur den Preis für ein einzelnes Produkt aktualisieren. Eine Aktualisierung des Massenpreises ist nicht verfügbar.

Denken Sie daran: freigegebene Kataloge nutzen die Preise der Kundengruppe.

**Verwandte Dokumentation**

* [Planen einer Aktualisierung (Content Staging)](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html) in unserem Benutzerhandbuch.
* [Erweiterte Preise](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) in unserem Benutzerhandbuch.

## Preisaktualisierung für Basispreis planen

Siehe den entsprechenden Artikel: [Wie wirkt sich die Änderung des Basispreises auf den gemeinsamen Katalogpreis aus?](/help/faq/general/base-price-change-affect-on-shared-catalog-price.md) in unserer Wissensdatenbank.
