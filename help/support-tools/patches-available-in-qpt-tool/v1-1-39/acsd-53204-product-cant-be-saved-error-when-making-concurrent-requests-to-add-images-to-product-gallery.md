---
title: "ACSD-53204: *Das Produkt kann nicht gespeichert werden* Fehler bei gleichzeitigen Anfragen zum Hinzufügen von Bildern zur Galerie."
description: Wenden Sie den Patch ACSD-53204 an, um das Adobe Commerce-Problem zu beheben, bei dem der Fehler *Das Produkt kann nicht gespeichert werden* ausgegeben wird, wenn gleichzeitige Anfragen zum Hinzufügen von Bildern zur Produktgalerie mit dem Endpunkt rest/V1/products/&lt;sku&gt;/media gestellt werden.
feature: Catalog Management, Media, Products, REST
role: Admin, Developer
exl-id: dcea2621-66cf-49d1-bba6-b61c70716e84
source-git-commit: e1ab32a4540ea7483f7f2b8464ef3e4b0ecbbac7
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-53204: &quot;*Das Produkt kann nicht gespeichert werden*&quot;-Fehler bei gleichzeitigen Anfragen zum Hinzufügen von Bildern zur Galerie

Der Patch ACSD-53204 behebt das Problem, bei dem *Das Produkt kann nicht gespeichert werden*&quot; wird bei gleichzeitigen Anfragen zum Hinzufügen von Bildern zur Produktgalerie mit der `rest/V1/products/<sku>/media` -Endpunkt. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.39 ist installiert. Die Patch-ID ist ACSD-53204. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

&quot;*Das Produkt kann nicht gespeichert werden*&quot; wird bei gleichzeitigen Anfragen zum Hinzufügen von Bildern zur Produktgalerie mit der `rest/V1/products/<sku>/media` -Endpunkt.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Admin Panel an.
1. Erstellen Sie ein Produkt mit SKU p1.
1. Mehrere gleichzeitige Anfragen an die `rest/V1/products/<sku>/media` Endpunkt zum gleichzeitigen Hochladen mehrerer Bilder.

<u>Erwartete Ergebnisse</u>:

Die Bilder werden fehlerfrei gespeichert.

<u>Tatsächliche Ergebnisse</u>:

&quot;*Das Produkt kann nicht gespeichert werden*&quot; von Zeit zu Zeit zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
