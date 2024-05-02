---
title: "MDVA-42584: Lagerstatus des konfigurierbaren Produkts nicht automatisch aktualisiert"
description: Der Patch MDVA-42584 behebt das Problem, dass der Lagerstatus des konfigurierbaren Produkts nicht automatisch aktualisiert wird, wenn sein einfaches Produkt aktualisiert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-42584. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: bf2697a2-8d15-408b-8d59-7b4173537e60
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-42584: Lagerstatus des konfigurierbaren Produkts nicht automatisch aktualisiert

Der Patch MDVA-42584 behebt das Problem, dass der Lagerstatus des konfigurierbaren Produkts nicht automatisch aktualisiert wird, wenn sein einfaches Produkt aktualisiert wird. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-42584. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Lagerstatus des konfigurierbaren Produkts im Backend wird nicht automatisch aktualisiert, wenn sein einfaches Produkt auf **Auf Lager** über API oder Import.

<u>Voraussetzungen</u>:

MSI installiert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen eines konfigurierbaren Produkts, **InvCheck001**, mit zwei Optionen: **InvCheck001-M** und **InvCheck001-L**.
1. Die einfachen Produkte sollten eine Menge haben und sie sollten **Auf Lager** damit auch das konfigurierbare Produkt **Auf Lager** im Backend.
1. Aktualisieren Sie jetzt sowohl einfache Produkte als auch setzen Sie Quantity auf **0** und Lagerstatus auf **Nicht vorrätig**.
1. Aktualisieren Sie das konfigurierbare Produkt und überprüfen Sie, ob der Lagerstatus aktualisiert wird auf **Nicht vorrätig**.
1. Verwenden Sie den folgenden API-Endpunkt und legen Sie das einfache Produkt fest **InvCheck001-M** nach **Auf Lager** mit Menge > 0.

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

1. Gehen Sie zum Backend und überprüfen Sie die Menge und den Lagerstatus des einfachen Produkts **InvCheck001-M**. Es wird aktualisiert auf **Auf Lager**.
1. Aktualisieren Sie das konfigurierbare Produkt und überprüfen Sie den Lagerstatus.

<u>Erwartete Ergebnisse</u>:

Der Lagerstatus des konfigurierbaren Produkts **InvCheck001** im Backend automatisch auf **Auf Lager**.

<u>Tatsächliche Ergebnisse</u>:

Der Lagerstatus des konfigurierbaren Produkts ist weiterhin **Nicht vorrätig**.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
