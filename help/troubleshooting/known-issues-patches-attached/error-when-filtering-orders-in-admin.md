---
title: Fehler beim Filtern von Bestellungen in Admin
description: Dieser Artikel enthält einen Patch für das Adobe Commerce-Problem, bei dem beim Versuch, Bestellungen im Admin nach Datum zu filtern, ein Fehler auftritt, der die Meldung "Integrity constraint verletzungen 1052 Column 'created_at', wobei die -Klausel mehrdeutig ist"anzeigt.
feature: Orders
role: Developer
source-git-commit: e5eb65b23afaed4658f8576c747f11a31a8ec1aa
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Fehler beim Filtern von Bestellungen in Admin

Dieser Artikel enthält einen Patch für das Adobe Commerce-Problem, bei dem beim Versuch, Bestellungen im Admin nach Datum zu filtern, ein Fehler auftritt und die Meldung angezeigt wird: *Verletzung der Integritätsbeschränkung: 1052 Spalte &#39;created_at&#39;, wobei der Satz mehrdeutig ist*.

## Betroffene Versionen

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7

## Problem

Beim Filtern von Bestellungen im Admin nach Datum wird ein Fehler zurückgegeben.

Die Ausnahme.log zeigt:

```SQL
report.CRITICAL: PDOException: SQLSTATE[23000]: Integrity constraint violation: 1052 Column 'created_at' in where clause is ambiguous in /path/to/magento/vendor/magento/framework/DB/Statement/Pdo/Mysql.php:90
```

<u>Zu reproduzierende Schritte:</u>

1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
   * Legen Sie die **[!UICONTROL Purchase Date Ascending]** -Reihenfolge im Raster fest, ODER
   * Legen Sie **[!UICONTROL Purchase Date Filter]** in Filtern fest.

1. Es wird ein Fehler angezeigt: *Bei der Verarbeitung der Standardansicht ist etwas schiefgelaufen, und wir haben den Originalzustand des Filters wiederhergestellt.*

## Ursache

Es gibt ein Problem mit den [!DNL PayPal Braintree] -Modulen.

## Lösung

Um das Problem zu lösen, wenden Sie den Patch an, der diesem Artikel beigefügt ist. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[bundle_3357_filter_order_in_admin_by_date_patch.zip](assets/bundle-3357-unable-to-filter-order-in-admin-by-date.zip)

Der Patch ist mit allen betroffenen Versionen und Editionen kompatibel.

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches in der Wissensdatenbank.
