---
title: 'MDVA-42584: Lagerstatus des konfigurierbaren Produkts nicht automatisch aktualisiert'
description: Der MDVA-42584 Patch löst das Problem, dass der Lagerstatus des konfigurierbaren Produkts nicht automatisch aktualisiert wird, wenn sein einfaches Produkt aktualisiert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-42584. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: bf2697a2-8d15-408b-8d59-7b4173537e60
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-42584: Lagerstatus des konfigurierbaren Produkts nicht automatisch aktualisiert

Der MDVA-42584 Patch löst das Problem, dass der Lagerstatus des konfigurierbaren Produkts nicht automatisch aktualisiert wird, wenn sein einfaches Produkt aktualisiert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-42584. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Lagerstatus des konfigurierbaren Produkts im Backend wird nicht automatisch aktualisiert, wenn sein einfaches Produkt über API oder Import auf **Auf Lager** eingestellt ist.

<u>Voraussetzungen</u>:

MSI installiert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein konfigurierbares Produkt, **InvCheck001**, mit zwei Optionen: **InvCheck001-M** und **InvCheck001-L**.
1. Beide einfachen Produkte sollten über „Menge“ verfügen und **„Auf Lager** sein, sodass das konfigurierbare Produkt auch **Auf Lager** im Backend ist.
1. Aktualisieren Sie jetzt sowohl die einfachen Produkte als auch die Menge auf **0** und den Lagerstatus auf **Nicht vorrätig**.
1. Aktualisieren Sie das konfigurierbare Produkt und überprüfen Sie, ob der Lagerstatus auf &quot;**&quot;**.
1. Verwenden Sie den folgenden API-Endpunkt und setzen Sie das einfache Produkt **InvCheck001-M** auf **Auf Lager** mit Menge > 0.

   ```JSON
   /rest/V1/inventory/source-items
   
   {
     "sourceItems":
     [
       {
         "sku": "InvCheck001-M",
         "source_code": "default",
         "quantity": 10,
         "status": 1
       }
     ]
   }
   ```

1. Gehen Sie zum Backend und überprüfen Sie die Menge und den Lagerstatus des einfachen Produkts **InvCheck001-M**. Es wird auf &quot;**&quot;**.
1. Aktualisieren Sie das konfigurierbare Produkt und überprüfen Sie den Lagerstatus.

<u>Erwartete Ergebnisse</u>:

Der Lagerstatus des konfigurierbaren Produkts **InvCheck001** im Backend wird automatisch auf &quot;**&quot;**.

<u>Tatsächliche Ergebnisse</u>:

Der Lagerstatus des konfigurierbaren Produkts ist weiterhin **Nicht vorrätig**.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
