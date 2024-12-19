---
title: 'MDVA-44533: Rabatt wurde falsch auf gebündeltes untergeordnetes Produkt angewendet'
description: Der Patch MDVA-44533 behebt das Problem, dass ein Rabatt fälschlicherweise auf ein gebündeltes untergeordnetes Produkt angewendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-44533. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: 84302ed4-d850-45e4-8b5b-44495f9df820
feature: Orders, Personalization, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-44533: Rabatt wurde falsch auf gebündeltes untergeordnetes Produkt angewendet

Der Patch MDVA-44533 behebt das Problem, dass ein Rabatt fälschlicherweise auf ein gebündeltes untergeordnetes Produkt angewendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-44533. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1 - 2.4.3-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Rabatt wird fälschlicherweise auf ein gebündeltes untergeordnetes Produkt angewendet.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein einfaches Produkt mit einem Preis von 50 $.
1. Erstellen Sie ein gebündeltes Produkt und weisen Sie das einfache Produkt als einzige Option für das gebündelte Produkt zu.
1. Erstellen Sie eine Warenkorb-Preisregel mit:

   * Bedingung: Wenn der Gesamtbetrag größer als 130 $ ist
   * Aktion: Es wird ein Festbetrag-Rabatt von 10 $ angewendet

1. Gehen Sie zur Storefront und fügen Sie das Bundle-Produkt mit der Menge = 1 in den Warenkorb.
1. Gehen Sie zum Warenkorb und überprüfen Sie, ob die Gesamtkosten des Bundle-Produkts 50 $ betragen und der Rabatt nicht zutrifft.
1. Ändern Sie die Menge in 2 und aktualisieren Sie den Warenkorb. Die Gesamtkosten für das gebündelte Produkt sollten jetzt 100 $ betragen.

<u>Erwartete Ergebnisse</u>:

Der Rabatt wird nicht angewendet, da die Zwischensumme 100\$ beträgt, was in der Regelbedingung weniger als 130\$ beträgt.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt wird angewendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in unserer Entwicklerdokumentation.
