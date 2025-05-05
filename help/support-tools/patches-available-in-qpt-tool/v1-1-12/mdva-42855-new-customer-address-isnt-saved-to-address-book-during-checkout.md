---
title: 'MDVA-42855: Beim Checkout wird keine neue Kundenadresse im Adressbuch gespeichert '
description: Mit dem Patch MDVA-42855 wird das Problem behoben, dass die neue Kundenadresse beim Checkout nicht im Adressbuch gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42855. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: 37fc51f4-773e-4bef-9fb1-e6629562b94a
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-42855: Beim Checkout wird keine neue Kundenadresse im Adressbuch gespeichert

Mit dem Patch MDVA-42855 wird das Problem behoben, dass die neue Kundenadresse beim Checkout nicht im Adressbuch gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42855. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die neue Kundenadresse wird beim Checkout nicht im Adressbuch gespeichert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Kundenkonto und aktualisieren Sie die standardmäßige Versand- und Rechnungsadresse.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und navigieren Sie zur Kasse .
1. Klicken Sie beim Versand auf **+ Neue Adresse**.
1. Geben Sie Ihre neue Adresse ein, und lassen Sie **Kontrollkästchen „Im Adressbuch**&quot; aktiviert.
1. Aktivieren Sie bei Zahlung das Kontrollkästchen **Meine Rechnungs- und Lieferadresse sind identisch**.
1. Bestellung aufgeben.
1. Schau ins Adressbuch.

<u>Erwartete Ergebnisse</u>:

Die neue Lieferadresse wird im Adressbuch gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Die neue Lieferadresse wird nicht im Adressbuch gespeichert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
