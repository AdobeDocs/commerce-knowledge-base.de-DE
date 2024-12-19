---
title: Fehler beim Filtern von Bestellungen im Admin-Bereich
description: In diesem Artikel erhalten Sie einen Patch für das Adobe Commerce-Problem, bei dem beim Versuch, Bestellungen im Admin nach Datum zu filtern, ein Fehler auftritt, der die Meldung „Integritätsbeschränkungsverletzung 1052 Spalte 'created_at', bei der die -Klausel mehrdeutig ist“ anzeigt.
feature: Orders
role: Developer
exl-id: 64aa104e-3b01-4a26-a88a-6aef06d9239e
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Fehler beim Filtern von Bestellungen im Admin-Bereich

In diesem Artikel erhalten Sie einen Patch für das Adobe Commerce-Problem, bei dem beim Versuch, Bestellungen im Admin nach Datum zu filtern, ein Fehler auftritt, der die folgende Meldung anzeigt: *Integritätsbeschränkungsverletzung: 1052 Spalte &#39;created_at&#39;, wobei die -Klausel mehrdeutig ist*.

## Betroffene Versionen

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7

## Problem

Beim Filtern der Bestellungen im Feld Admin nach Datum wird ein Fehler zurückgegeben.

Exception.log zeigt:

```SQL
report.CRITICAL: PDOException: SQLSTATE[23000]: Integrity constraint violation: 1052 Column 'created_at' in where clause is ambiguous in /path/to/magento/vendor/magento/framework/DB/Statement/Pdo/Mysql.php:90
```

<u>Schritte zur Reproduktion:</u>

1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
   * **[!UICONTROL Purchase Date Ascending]** Reihenfolge im Raster festlegen, ODER
   * **[!UICONTROL Purchase Date Filter]** in Filtern festlegen.

1. Ein Fehler wird angezeigt: *Bei der Verarbeitung der Standardansicht ist ein Fehler aufgetreten, und der Filter wurde in den Originalzustand zurückversetzt.*

## Ursache

Es gibt ein Problem mit den [!DNL PayPal Braintree].

## Lösung

Um das Problem zu beheben, wenden Sie den Patch an, der diesem Artikel beigefügt ist. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[bundle_3357_filter_order_in_admin_by_date_patch.zip](assets/bundle-3357-unable-to-filter-order-in-admin-by-date.zip)

Der Patch ist mit allen betroffenen Versionen und Editionen kompatibel.

## Anbringen des Pflasters

Anweisungen finden Sie unter [Anwenden eines Composer-Patches von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in der Support-Wissensdatenbank.
