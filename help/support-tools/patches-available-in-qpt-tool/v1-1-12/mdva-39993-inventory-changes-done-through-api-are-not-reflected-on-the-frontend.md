---
title: "MDVA-39993: Über API vorgenommene Bestandsänderungen werden in Storefront nicht berücksichtigt"
description: Der Patch MDVA-39993 behebt das Problem, dass die durch die API vorgenommenen Bestandsänderungen nicht in der Storefront angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-39993. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: 2d49b9b7-8a70-44f3-80bf-4460bb2e61d5
feature: REST, Inventory, Orders, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---

# MDVA-39993: Über API durchgeführte Bestandsänderungen werden nicht auf der Storefront angezeigt

Der Patch MDVA-39993 behebt das Problem, dass die durch die API vorgenommenen Bestandsänderungen nicht in der Storefront angezeigt werden. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-39993. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5 - 2.3.7-p2 und 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Bestandsänderungen, die über die API vorgenommen werden, werden nicht auf der Produktseite der Storefront angezeigt.

<u>Voraussetzungen</u>:

Inventarmodule installiert.

<u>Zu reproduzierende Schritte</u>:

1. Stellen Sie sicher, dass die Warteschlange so eingestellt ist, dass sie mit Cron ausgeführt wird und Cron installiert und ausgeführt wird.
1. Erstellen Sie ein konfigurierbares Produkt (COC001) mit zwei Farben (Schwarz und Rot) und zwei Größen (M und L).
1. Eine Option aus dem Lager entfernen (COC001-Red-M).
1. Laden Sie die konfigurierbare Produktseite in die Storefront und versuchen Sie, auf jede Farbe zu klicken. Wenn Sie auf **Rot**, die Größe **M** sollte gestrichen werden, weil es nicht vorrätig ist.
1. Machen Sie COC001-Red-M mit dem folgenden API-Endpunkt und der Payload auf Lager:

   ```json
   POST http://{domain}/rest/V1/inventory/source-items
   
   {
     "sourceItems": [
       {
         "sku": "COC001-Red-M",
         "source_code": "default",
         "quantity": 1000,
         "status": 1
       }
     ]
   }
   ```

1. Überprüfen Sie dieses einfache Produkt aus dem Backend und stellen Sie sicher, dass es auf &quot;In Stock&quot;aktualisiert wurde.
1. Laden Sie das konfigurierbare Produkt vom Frontend und klicken Sie auf jede Farbe. Beachten Sie die Größe **M** beim Klicken auf **Rot**.

<u>Erwartete Ergebnisse</u>:

Die Option COC001-Red-M ist nicht durchkreuzt, da sie über die API auf In Stock aktualisiert wurde.

<u>Tatsächliche Ergebnisse</u>:

Die Option COC001-Red-M ist immer noch ausgekreuzt, obwohl sie auf Lager ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
