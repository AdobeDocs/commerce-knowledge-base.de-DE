---
title: Aktualisierung auf das DHL-Schema v10, um DHL-Versand weiterhin anzubieten
description: Dieser Artikel bietet eine Lösung, die es Händlern ermöglicht, den DHL-Versand weiterhin anzubieten, nachdem das DHL-Schema 6.2 im Dezember 2022 eingestellt wurde, indem ein Upgrade auf Schema 10.0 durchgeführt oder der AC-3023-Patch angewendet wird.
exl-id: eed83713-2d6a-4360-bfa1-bebd4d604f2f
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# Aktualisierung auf DHL-Schema Version 10.0, um DHL-Versand weiterhin anzubieten

Dieser Artikel bietet eine Lösung, die es Händlern ermöglicht, DHL-Sendungen weiterhin anzubieten, nachdem die DHL-Schemaversion 6.2 Ende Dezember 2022 eingestellt wurde.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.5 und frühere Versionen, alle Implementierungsmethoden.

## Problem

Im August 2022 haben wir die [Aktualisierung des DHL-Schemas Version 6.2 zusammen mit einem Patch für die Fehlerbehebung](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html) für Händler, um weiterhin DHL-Versand anzubieten. DHL führt im Oktober 2022 erneut ein neueres Schema - Version 10.0 - ein, und die vorherige Version (Schema 6.2) wird Ende Dezember 2022 eingestellt. Die DHL-Integration von Adobe Commerce 2.4.5 und früher unterstützt nur Version 6.2.

## Lösung

Adobe Commerce 2.4.5-p1 und 2.4.4-p2, die im Oktober 2022 veröffentlicht wurden, enthalten die neue DHL-Schemaversion 10.0. Händler, die auf 2.4.5-p1 und 2.4.4-p2 aktualisieren, müssen also nichts tun, um die DHL-Sendungen weiterhin anzubieten. Wir empfehlen allen Händlern, vor der Einstellung des DHL-Schemas 6.2 Ende Dezember 2022 auf 2.4.5-p1 und 2.4.4-p2 zu aktualisieren.

Händler, die nicht auf 2.4.5-p1 und 2.4.4-p2 aktualisieren möchten, müssen einen Patch installieren, wenn sie DHL-Versand nach Dezember 2022 weiterhin anbieten möchten.

## Patch

Die Patch-ID ist AC-3023 und ist im [!DNL Quality Patches Tool] Version 1.1.21.

Unter den folgenden Links erfahren Sie, wie Sie [!DNL Quality Patches Tool] und installieren Sie Patches je nach Ihren Bereitstellungsmethoden:

* Adobe Commerce vor Ort und Magento Open Source: [Tools für Qualitätsmuster > Verwendung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in Adobe Experience League.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

**Der Patch gilt für die folgenden Adobe Commerce-Versionen (alle Bereitstellungsmethoden):**

* 2.3.7, 2.4.0, 2.4.1, 2.4.2, 2.4.3, 2.4.3-p2, 2.4.3-p3, 2.4.4

## Nützliche Links

* [[!DNL Quality Patches Tool] > Versionshinweise](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) in Adobe Experience League.

* [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in Adobe Experience League.

## Verwandtes Lesen

* [Wenden Sie einen Patch an, um DHL weiterhin als Versandunternehmen anzubieten.](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html) in unserer Wissensdatenbank.

* [Versandunternehmen > DHL](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/shipping-carriers/dhl.html) in unserem Benutzerhandbuch.
* [Configuration Reference > Sales > Delivery Methods](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/delivery-methods.html) in unserem Benutzerhandbuch.
