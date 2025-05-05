---
title: Upgrade auf v10 DHL-Schema, um weiterhin DHL-Versand anbieten zu können
description: Dieser Artikel bietet eine Lösung, mit der Händler weiterhin DHL-Versand anbieten können, nachdem das DHL-Schema 6.2 im Dezember 2022 eingestellt wurde, indem sie auf Schema 10.0 aktualisieren oder den AC-3023-Patch anwenden.
exl-id: eed83713-2d6a-4360-bfa1-bebd4d604f2f
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# Upgrade auf das DHL-Schema Version 10.0, um weiterhin DHL-Versand anbieten zu können

Dieser Artikel bietet eine Lösung, mit der Händler weiterhin DHL-Versand anbieten können, nachdem das DHL-Schema Version 6.2 Ende Dezember 2022 eingestellt wurde.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.5 und frühere Versionen, alle Bereitstellungsmethoden.

## Problem

Im August 2022 haben wir das [Upgrade von DHL Schema Version 6.2. zusammen mit einem Fix Patch](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html?lang=de) veröffentlicht, damit Händler weiterhin DHL-Versand anbieten können. DHL führt im Oktober 2022 erneut ein neueres Schema ein - Version 10.0 -, und die vorherige Version (Schema 6.2) wird Ende Dezember 2022 eingestellt. Die Integration von Adobe Commerce 2.4.5 und früheren DHL-Versionen unterstützt nur Version 6.2.

## Lösung

Adobe Commerce 2.4.5-p1 und 2.4.4-p2, veröffentlicht im Oktober 2022, enthalten die neue DHL-Schemaversion 10.0. Händler, die auf 2.4.5-p1 und 2.4.4-p2 aktualisieren, müssen also nichts tun, um weiterhin die DHL-Sendungen anbieten zu können. Wir empfehlen allen Händlern, vor der Einstellung von DHL-Schema 6.2 bis Ende Dezember 2022 ein Upgrade auf 2.4.5-p1 und 2.4.4-p2 durchzuführen.

Händler, die nicht auf die Versionen 2.4.5-p1 und 2.4.4-p2 aktualisieren möchten, müssen einen Fix-Patch anwenden, wenn sie nach Dezember 2022 weiterhin DHL-Versand anbieten möchten.

## Fleck

Die Patch-ID ist AC-3023 und in der [!DNL Quality Patches Tool] Version 1.1.21 verfügbar.

Siehe die folgenden Links für die Verwendung von [!DNL Quality Patches Tool] und die Installation von Patches entsprechend Ihren Bereitstellungsmethoden:

* Adobe Commerce On-Premise und Magento Open Source: [Quality Patches Tools > Usage](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) in Adobe Experience League.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

**Der Patch gilt für die folgenden Adobe Commerce-Versionen (alle Bereitstellungsmethoden):**

* 2.3.7, 2.4.0, 2.4.1, 2.4.2, 2.4.3, 2.4.3-P2, 2.4.3-P3, 2.4.4

## Nützliche Links

* [[!DNL Quality Patches Tool] > Versionshinweise](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html?lang=de) in Adobe Experience League.

* [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in Adobe Experience League.

## Verwandtes Lesen

* [Wenden Sie einen Patch an, um DHL weiterhin als ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html?lang=de) in unserer Support-Wissensdatenbank anzubieten.

* [Spedition > DHL](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/shipping-carriers/dhl.html?lang=de) in unserem Benutzerhandbuch.
* [Konfigurationsreferenz > Vertrieb > Liefermethoden](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/delivery-methods.html?lang=de) in unserem Benutzerhandbuch.
