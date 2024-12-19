---
title: Patch anwenden, um DHL weiterhin als Versandunternehmen anzubieten
description: Dieser Artikel enthält einen Patch, mit dem Händler, die Adobe Commerce 2.4.4 und früher verwenden, weiterhin DHL-Versand anbieten können, nachdem das DHL-Schema 6.0 Ende Juli bis September 2022 eingestellt wurde.
exl-id: 4350e83a-495b-41b4-a526-dae5923e9d41
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Patch anwenden, um DHL weiterhin als Versandunternehmen anzubieten


## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.4 und früher, alle Bereitstellungsmethoden.

## Problem

DHL führt eine 6.2-Schemaversion ein und stellt Version 6.0 Ende Juli bis September 2022 ein. Adobe Commerce 2.4.4 und frühere DHL-Integration unterstützt nur Version 6.0.

## Lösung

Adobe Commerce 2.4.5, die im August 2022 veröffentlicht werden soll, wird die aktualisierte Integration mit DHL unter Verwendung des Schemas Version 6.2 enthalten. Bis die neue Version veröffentlicht wird (oder falls Sie sich gegen ein Upgrade entscheiden), empfehlen wir Ihnen, den AC-3022-Patch anzuwenden, der die Unterstützung des DHL-Schemas der Version 6.2 implementiert, um nach der Einstellung weiterhin DHL-Sendungen in Ihrem Geschäft anbieten zu können.

## Fleck

Die Patch-ID ist AC-3022 und steht im Quality Patches Tool Version 1.1.16 zur Verfügung.
Informationen zur Verwendung [ QPT und zur Installation von Patches finden Sie ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) Artikel „Quality Patches Tool (QPT) > Usage“ in unserer Entwicklerdokumentation.

Der Patch gilt für die folgenden Adobe Commerce-Versionen:

* 2.4.0 - 2.4.4-p1
* 2,3,7

## Verwandtes Lesen

* [Spedition > DHL](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/delivery/shipping-carriers/dhl) in unserem Benutzerhandbuch
* [Versandmethoden](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/delivery-methods) in unserem Benutzerhandbuch
