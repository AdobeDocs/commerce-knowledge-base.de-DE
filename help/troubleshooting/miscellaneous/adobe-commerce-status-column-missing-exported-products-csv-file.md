---
title: In der Adobe Commerce-Statusspalte fehlt die exportierte Produkt-CSV-Datei
description: Dieser Artikel bietet eine Lösung für das Problem, wenn Sie die Statusspalte in der CSV-Datei mit exportierten Produkten nicht finden können.
exl-id: 3cbe1e6c-fc73-4331-add7-1ebcb28a4580
feature: Data Import/Export, Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# In der Adobe Commerce-Statusspalte fehlt die exportierte Produkt-CSV-Datei

Dieser Artikel bietet eine Lösung für das Problem, wenn Sie die Statusspalte (d. h. die Angabe, ob das Produkt aktiviert oder deaktiviert ist) in der CSV-Datei, die exportierte Produkte enthält, nicht finden können. Der Status des Produkts wird durch die Spalte [!UICONTROL product_online] angezeigt.

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) - alle [unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problem

Die [!UICONTROL status] Spalte kann nicht in der CSV-Datei gefunden werden, die exportierte Produkte enthält. Sie exportieren also beispielsweise eine CSV-Datei aller SKUs mit ihrem Status, aber der Tabelle scheint die [!UICONTROL status] Spalte zu fehlen.

<u>Schritte zur Reproduktion:</u>

1. Wählen Sie in Adobe Commerce Admin die Option **[!UICONTROL System]** und **[!UICONTROL Data Transfer]** dann **[!UICONTROL Export]** aus.
1. Wählen Sie im **[!UICONTROL Export Settings]** Abschnitt die Option in der Dropdown-**[!UICONTROL Products]** **[!UICONTROL Entity Type]** aus.
1. Suchen Sie nach **[!UICONTROL status]**, die unter **[!UICONTROL Attribute Code]** aufgeführt sind. Dieser Attributcode wird in der Liste der verfügbaren Attribute angezeigt (**[!UICONTROL Enable Product]**).
1. Klicken Sie auf **[!UICONTROL Export]**.

<u>Erwartetes Ergebnis:</u>

In der soeben exportierten CSV-Datei wird eine Spalte mit der Bezeichnung [!UICONTROL status] angezeigt.

<u>Tatsächliches Ergebnis:</u>

In der exportierten CSV-Datei wird keine Spalte mit der Bezeichnung [!UICONTROL status] angezeigt.

## Ursache

Das Statusattribut des Produkts wurde in der CSV-Datei umbenannt. Sie ist jetzt die Spalte [!UICONTROL product_online] .

## Lösung

1. Wählen Sie **[!UICONTROL System]** und unter **[!UICONTROL Data Transfer]** wählen Sie **[!UICONTROL Import]** aus.
1. Klicken Sie auf **[!UICONTROL Download Sample File]**.
1. Die Spalte [!UICONTROL product_online] wird in der CSV-Datei angezeigt.

## Verwandtes Lesen

* [Arbeiten mit CSV-](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/data-transfer/data-csv) in unserem Benutzerhandbuch.
* [Produktexport-Attribute-Referenz](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/data-transfer/data-attributes-product) in unserem Benutzerhandbuch.
