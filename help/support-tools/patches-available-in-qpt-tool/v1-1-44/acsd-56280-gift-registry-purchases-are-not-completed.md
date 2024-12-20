---
title: 'ACSD-56280: Geschenkkäufe in der Registrierung sind nicht abgeschlossen'
description: Wenden Sie den Patch ACSD-56280 an, um das Adobe Commerce-Problem zu beheben, bei dem die Käufe der Geschenkregistrierung nicht abgeschlossen sind.
feature: Checkout
role: Admin
exl-id: 8e78ea1d-bd55-49d7-9d74-748b8f90e28c
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-56280: Geschenkkäufe in der Registrierung sind nicht abgeschlossen

Der Patch ACSD-56280 behebt das Problem, dass die Käufe der Geschenkregistrierung nicht abgeschlossen sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 installiert ist. Die Patch-ID ist ACSD-56280. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Käufe der Geschenkregistrierung sind noch nicht abgeschlossen.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich als Kunde an und fügen Sie eine **[!UICONTROL product]** zur Geschenkregistrierung hinzu.
1. Geben Sie den Link zur Geschenkregistrierung frei.
1. Öffnen Sie den Link zur Geschenkregistrierung in einem anderen Browser/Inkognito-Fenster.
1. Fügen Sie die Menge hinzu und fügen Sie die Artikel zum Warenkorb hinzu.
1. Klicken Sie auf &quot;**[!UICONTROL Checkout Page]**&quot;, wählen Sie &quot;**[!UICONTROL shipping method]**&quot;(Da die Versandadresse bereits ausgewählt ist, wird sie vom Registrierenden bereitgestellt).
1. Wählen Sie die Zahlungsmethode aus.
1. Klicken Sie auf die Schaltfläche Bestellung platzieren .

<u>Erwartete Ergebnisse</u>:

Die Bestellung sollte aufgegeben werden.

<u>Tatsächliche Ergebnisse</u>:

Die Reihenfolge wird nicht platziert, und der angezeigte Fehler lautet `Call to a member function getUpdatedQty() on null`.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
