---
title: Adobe Commerce-Statusspalte fehlt exportierte Produkt-CSV-Datei
description: Dieser Artikel bietet eine Lösung für das Problem, wenn Sie die Statusspalte in der CSV-Datei, die exportierte Produkte enthält, nicht finden können.
exl-id: 3cbe1e6c-fc73-4331-add7-1ebcb28a4580
feature: Data Import/Export, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Adobe Commerce-Statusspalte fehlt exportierte Produkt-CSV-Datei

Dieser Artikel bietet eine Lösung für das Problem, wenn Sie die Statusspalte (d. h. Angabe, ob das Produkt aktiviert oder deaktiviert ist) nicht in der CSV-Datei mit den exportierten Produkten finden können. Der Status des Produkts wird durch die Spalte [!UICONTROL product_online] angegeben.

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) alle [unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problem

Sie können die Spalte [!UICONTROL status] nicht in der CSV-Datei mit den exportierten Produkten finden. Sie exportieren beispielsweise eine CSV-Datei aller SKUs mit ihrem Status, der Tabelle fehlt jedoch die Spalte [!UICONTROL status] .

<u>Zu reproduzierende Schritte:</u>

1. Wählen Sie im Adobe Commerce-Admin **[!UICONTROL System]** unter **[!UICONTROL Data Transfer]** die Option **[!UICONTROL Export]** aus.
1. Wählen Sie im Abschnitt **[!UICONTROL Export Settings]** im Dropdown-Menü **[!UICONTROL Entity Type]** die Option **[!UICONTROL Products]** aus.
1. Suchen Sie nach &quot;**[!UICONTROL status]**&quot;, aufgeführt unter &quot;**[!UICONTROL Attribute Code]**&quot;. Sie sehen diesen Attributcode in der Liste der verfügbaren Attribute (**[!UICONTROL Enable Product]**).
1. Klicken Sie auf **[!UICONTROL Export]**.

<u>Erwartetes Ergebnis:</u>

In der soeben exportierten CSV-Datei sehen Sie eine Spalte mit der Bezeichnung [!UICONTROL status].

<u>Tatsächliches Ergebnis:</u>

In der exportierten CSV-Datei wird keine Spalte mit der Bezeichnung [!UICONTROL status] angezeigt.

## Ursache

Das Statusattribut des Produkts wurde in der CSV-Datei umbenannt. Dies ist nun die Spalte &quot;[!UICONTROL product_online]&quot;.

## Lösung

1. Wählen Sie &quot;**[!UICONTROL System]**&quot;, unter &quot;**[!UICONTROL Data Transfer]**&quot;die Option &quot;**[!UICONTROL Import]**&quot;.
1. Klicken Sie auf **[!UICONTROL Download Sample File]**.
1. Sie können die Spalte [!UICONTROL product_online] in der CSV-Datei sehen.

## Verwandtes Lesen

* [Arbeiten mit CSV-Dateien](https://docs.magento.com/user-guide/system/data-csv.html) in unserem Benutzerhandbuch.
* [Referenz zu Produktexport-Attributen](https://docs.magento.com/user-guide/system/data-attributes-product.html) in unserem Benutzerhandbuch.
