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

Dieser Artikel bietet eine Lösung für das Problem, wenn Sie die Statusspalte (d. h. Angabe, ob das Produkt aktiviert oder deaktiviert ist) nicht in der CSV-Datei mit den exportierten Produkten finden können. Der Status des Erzeugnisses wird durch die [!UICONTROL product_online] Spalte.

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) alle [unterstützte Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problem

Sie können die [!UICONTROL status] in der CSV-Datei, die exportierte Produkte enthält. Beispiel: Sie exportieren eine CSV-Datei aller SKUs mit ihrem Status, aber der Tabelle scheint die [!UICONTROL status] Spalte.

<u>Zu reproduzierende Schritte:</u>

1. Wählen Sie in Adobe Commerce Admin die Option **[!UICONTROL System]**, unter **[!UICONTROL Data Transfer]** select **[!UICONTROL Export]**.
1. Im **[!UICONTROL Export Settings]** auf der Registerkarte **[!UICONTROL Entity Type]** Dropdown **[!UICONTROL Products]**.
1. Suchen Sie nach **[!UICONTROL status]**, aufgeführt unter **[!UICONTROL Attribute Code]**. Sie sehen diesen Attributcode in der Liste der verfügbaren Attribute (**[!UICONTROL Enable Product]**).
1. Klicken Sie auf **[!UICONTROL Export]**.

<u>Erwartetes Ergebnis:</u>

In der soeben exportierten CSV-Datei wird eine Spalte mit der Bezeichnung [!UICONTROL status].

<u>Ergebnis:</u>

Es wird keine Spalte mit der Beschriftung [!UICONTROL status] in der exportierten CSV-Datei.

## Ursache

Das Statusattribut des Produkts wurde in der CSV-Datei umbenannt. Es ist jetzt [!UICONTROL product_online] Spalte.

## Lösung

1. Auswählen **[!UICONTROL System]**, unter **[!UICONTROL Data Transfer]** select **[!UICONTROL Import]**.
1. Klicks **[!UICONTROL Download Sample File]**.
1. Sie können die [!UICONTROL product_online] in der CSV-Datei.

## Verwandtes Lesen

* [Arbeiten mit CSV-Dateien](https://docs.magento.com/user-guide/system/data-csv.html) in unserem Benutzerhandbuch.
* [Produktexport-Attribute - Referenz](https://docs.magento.com/user-guide/system/data-attributes-product.html) in unserem Benutzerhandbuch.
