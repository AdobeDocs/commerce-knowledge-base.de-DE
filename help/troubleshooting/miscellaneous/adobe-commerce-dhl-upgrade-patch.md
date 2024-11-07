---
title: Wenden Sie einen Patch an, um DHL weiterhin als Versandunternehmen anzubieten.
description: Dieser Artikel enthält einen Patch, mit dem Händler, die Adobe Commerce 2.4.4 und früher verwenden, weiterhin DHL-Sendungen anbieten können, nachdem das DHL-Schema 6.0 Ende Juli - September 2022 eingestellt wurde.
exl-id: 4350e83a-495b-41b4-a526-dae5923e9d41
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Wenden Sie einen Patch an, um DHL weiterhin als Versandunternehmen anzubieten.


## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.4 und früher, alle Implementierungsmethoden.

## Problem

DHL führt eine Schemaversion von Version 6.2 ein und stellt Version 6.0 Ende Juli - September 2022 ein. Die DHL-Integration von Adobe Commerce 2.4.4 und früher unterstützt nur Version 6.0.

## Lösung

Adobe Commerce 2.4.5, die im August 2022 veröffentlicht werden soll, enthält die aktualisierte Integration mit DHL unter Verwendung des Schemas der Version 6.2. Bis die neue Version veröffentlicht wird (oder falls Sie sich gegen eine Aktualisierung entscheiden), empfehlen wir Ihnen, den Patch AC-3022 anzuwenden, der die DHL-Schemaunterstützung der Version 6.2 implementiert, um DHL-Sendungen nach der Einstellung weiterhin in Ihrem Geschäft anzubieten.

## Patch

Die Patch-ID ist AC-3022 in der Version 1.1.16 des Quality Patches Tool verfügbar.
Informationen zur Verwendung von QPT und zur Installation von Patches finden Sie im Artikel [Qualitätspatches-Tool (QPT) > Nutzung](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) unserer Entwicklerdokumentation.

Der Patch gilt für die folgenden Adobe Commerce-Versionen:

* 2.4.0 - 2.4.4 - p1
* 2,3,7

## Verwandtes Lesen

* [Versandunternehmen > DHL](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/delivery/shipping-carriers/dhl) in unserem Benutzerhandbuch
* [Bereitstellungsmethoden](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/delivery-methods) in unserem Benutzerhandbuch
