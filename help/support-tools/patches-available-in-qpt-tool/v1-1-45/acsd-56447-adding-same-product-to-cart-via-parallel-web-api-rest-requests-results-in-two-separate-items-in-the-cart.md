---
title: "ACSD-56447: Das Hinzufügen desselben Produkts zum Warenkorb über die parallele Web-REST-API führt zu zwei separaten Artikeln im Warenkorb."
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

Der Patch ACSD-56447 behebt das Problem, dass das Hinzufügen desselben Produkts zum Warenkorb über parallele Web-REST-API-Anfragen zu zwei separaten Artikeln im Warenkorb führt. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 ist installiert. Die Patch-ID ist ACSD-56447. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn Sie dasselbe Produkt über parallele Web-REST-API-Anfragen zum Warenkorb hinzufügen, werden zwei separate Artikel im Warenkorb angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Generieren Sie ein Kunden-Token, um die REST-API-Aufrufanforderung mit [!DNL Postman].
1. Erstellen Sie einen Warenkorb für den Kunden.
1. Verwenden Sie das oben generierte Token, um einen leeren Warenkorb für den Kunden zu erstellen.
1. Verwenden Sie CURL, um zwei zu erstellen `AddProductsToCart` Anforderungen parallel ausgeführt werden. Befolgen Sie die Anweisungen im Abschnitt [Tutorial zur Bestellverarbeitung](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/) in der Entwicklerdokumentation.

<u>Erwartete Ergebnisse</u>:

Artikel mit mehreren Mengen werden in einer Zeile angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Dieselben SKUs werden in mehreren Zeileneinträgen angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
