---
title: "ACSD-49480: Nachfolgende Regeln verwerfen funktioniert nicht"
description: Wenden Sie den Patch ACSD-49480 an, um das Adobe Commerce-Problem zu beheben, bei dem das [!UICONTROL Cart Price Rule - Discard Subsequent Rules] funktioniert nicht wie beabsichtigt.
exl-id: 8d306a9e-ed1a-4295-8130-81700cbf31a6
feature: Price Rules
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-49480: [!UICONTROL Cart Price Rule - Discard Subsequent Rules] funktioniert nicht wie beabsichtigt

Der Patch ACSD-49480 behebt das Problem, bei dem das [!UICONTROL Cart Price Rule - Discard Subsequent Rules] funktioniert nicht wie beabsichtigt. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.32 installiert ist. Die Patch-ID lautet ACSD-49480. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

[!UICONTROL Cart Price Rule - Discard Subsequent Rules] funktioniert nicht wie beabsichtigt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine **[!UICONTROL Cart Price Rule]** mit Couponcode (nennen Sie ihn *TEST*), der einen Rabatt von 10 USD für die *Produkt-ID 1* im **[!UICONTROL Actions]** Registerkarte mit [!UICONTROL Discard Subsequent Rules] auf *[!UICONTROL Yes]* und [!UICONTROL Priority] auf *1*.
1. Erstellen eines weiteren **[!UICONTROL Cart Price Rule]** ohne Couponcode, der einen Rabatt von 5 USD gewährt *Produkt-ID 2* im **[!UICONTROL Actions]** Registerkarte mit [!UICONTROL Priority] auf *2*. Hier nehmen wir an, dies ist ein globaler Verkauf für *Produkt-ID 2*.
1. Gehen Sie zur Frontend-Site und fügen Sie *Produkt-ID 1* und *Produkt-ID 2* in den Warenkorb.
1. Wenden Sie die *TEST* Couponcode.

<u>Erwartete Ergebnisse</u>

* *Rabatt 1* wird angewendet auf *Produkt-ID 1*.
* *Rabatt 2* wird angewendet auf *Produkt-ID 2*.

<u>Tatsächliche Ergebnisse</u>

* Nur *Rabatt 1* wird angewendet auf *Produkt-ID 1*.
* *Rabatt 2* wird nicht angewendet auf *Produkt-ID 2*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
