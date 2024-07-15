---
title: "ACSD-52398: Angeforderte Menge nicht verfügbar, wenn versucht wird, die Menge des gebündelten Produkts zu aktualisieren"
description: Wenden Sie den Patch ACSD-52398 an, um das Adobe Commerce-Problem zu beheben, bei dem die angeforderte Menge nicht verfügbar ist, wenn versucht wird, die Menge eines gebündelten Produkts im Warenkorb auf der Storefront zu aktualisieren.
feature: Shopping Cart, Quotes, Products
role: Admin
exl-id: 7b7f06ac-7913-4603-992a-a5620045d828
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-52398: Angeforderte Menge nicht verfügbar, wenn versucht wird, die Menge des gebündelten Produkts zu aktualisieren

Der Patch ACSD-52398 behebt das Problem, dass die angeforderte Menge nicht verfügbar ist, wenn versucht wird, die Menge eines gebündelten Produkts im Warenkorb auf der Storefront zu aktualisieren. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-52398. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die angeforderte Menge ist nicht verfügbar, wenn versucht wird, die Menge eines gebündelten Produkts im Warenkorb auf der Storefront zu aktualisieren.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie zwei einfache Produkte mit den Mengen *1* und *10*.
1. Erstellen Sie ein gebündeltes Produkt mit den einfachen Produkten.
1. Fügen Sie das gebündelte Produkt zum Warenkorb hinzu.
1. Bearbeiten Sie das Produkt und versuchen Sie, die Menge für die Option, bei der *10* Elemente verfügbar sind, auf *3* zu aktualisieren.

<u>Erwartete Ergebnisse</u>:

Es gibt keinen Fehler. Die Menge wurde erfolgreich aktualisiert, da für diese Option *10* Elemente auf Lager sind.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler wird ausgegeben: *Die angeforderte Menge ist nicht verfügbar*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
