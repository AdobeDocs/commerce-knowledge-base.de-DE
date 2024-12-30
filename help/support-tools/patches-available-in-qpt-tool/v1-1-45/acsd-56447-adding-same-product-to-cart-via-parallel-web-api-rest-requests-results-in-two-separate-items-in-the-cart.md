---
title: 'ACSD-56447: Das Hinzufügen desselben Produkts zum Warenkorb über die parallele Web-REST-API führt zu zwei separaten Artikeln im Warenkorb'
description: Wenden Sie den Patch ACSD-56447 an, um das Adobe Commerce-Problem zu beheben, bei dem das Hinzufügen desselben Produkts zum Warenkorb über parallele Web-REST-API-Anfragen zu zwei separaten Artikeln im Warenkorb führt.
feature: Shopping Cart, REST
role: Admin, Developer
exl-id: c63874be-a8a6-4143-adaa-ba3e9e107dd4
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-56447: Das Hinzufügen desselben Produkts zum Warenkorb über die parallele Web-REST-API führt zu zwei separaten Artikeln im Warenkorb

Der Patch ACSD-56447 behebt das Problem, dass das Hinzufügen desselben Produkts zum Warenkorb über parallele Web-REST-API-Anfragen zu zwei separaten Artikeln im Warenkorb führt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 installiert ist. Die Patch-ID ist ACSD-56447. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Hinzufügen desselben Produkts zum Warenkorb über parallele Web-REST-API-Anfragen führt zu zwei separaten Artikeln im Warenkorb.

<u>Schritte zur Reproduktion</u>:

1. Generieren Sie ein Kunden-Token für die REST-API-Aufrufanforderung mit [!DNL Postman].
1. Erstellen Sie einen Warenkorb für den Kunden.
1. Verwenden Sie das oben generierte Token, um einen leeren Warenkorb für den Kunden zu erstellen.
1. Verwenden Sie CURL, um zwei `AddProductsToCart` parallel auszuführen. Befolgen Sie die Anweisungen im Tutorial [Bestellabwicklung](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/) in der Entwicklerdokumentation.

<u>Erwartete Ergebnisse</u>:

Artikel mit mehreren Mengen werden in einer Zeile angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Dieselben SKUs werden in mehreren Zeileneinträgen angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
