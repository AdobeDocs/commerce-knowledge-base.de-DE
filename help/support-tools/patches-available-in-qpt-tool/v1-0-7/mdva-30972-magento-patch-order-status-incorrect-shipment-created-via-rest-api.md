---
title: "MDVA-30972: Bestellstatus: inkorrekter Versand über REST API erstellt"
description: Der Patch MDVA-30972 löst das Problem, dass der Bestellstatus bei der Versanderstellung über die REST-API falsch geändert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 installiert ist.
exl-id: 70b8db1f-16d0-48f4-b0a2-483a7176cb89
feature: REST, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# MDVA-30972: über die REST API erstellte falsche Lieferung von Bestellstatus

Der Patch MDVA-30972 löst das Problem, dass der Bestellstatus bei der Versanderstellung über die REST-API falsch geändert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 installiert ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 bis 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn eine partielle Sendung von Admin über die REST-API für eine Bestellung mit dem Bestellstatus *Verdächtiger Betrug* erstellt wird, wird der Auftragsstatus in *Verarbeitung* geändert. Sie sollte bei *Verdächtiger Betrug* bleiben.

<u>Voraussetzungen</u>:

* PayPal EC oder eine andere Online-Zahlungsmethode eingerichtet.
* Die Integration für die REST-API ist eingerichtet.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Bestellung mit zwei oder mehr Elementen.
1. Melden Sie sich bei **Admin** > **Vertrieb** > **Bestellungen** an. Öffnen Sie die soeben erstellte Bestellung.
1. Scrollen Sie auf der Bestelldetailseite nach unten zu **Bestellsumme**. Klicken Sie auf die Dropdownliste **Status** und wählen Sie *Verdächtiger Betrug* aus. Klicken Sie dann auf die Schaltfläche **Kommentar senden** .
1. Vergewissern Sie sich, dass die Bestellung jetzt den Status *Verdächtiger Betrug* aufweist.
1. Erstellen Sie eine Sendung für einen Artikel aus der Bestellung mithilfe der REST-API:

   ```
   * Method = `Post`
   * Header = `"{host}/rest/V1/orders/ {order_id}/ship"`
   * Body =
   ```

   ```
    {      "items": [        {          "extension_attributes": {},          "order_item_id": {order_item_id},          "qty": 1        }      ]    }
   ```

1. Öffnen Sie die Bestellung erneut in Admin und überprüfen Sie den Status.

<u>Erwartete Ergebnisse</u>:

* Bestellstatus = *Verdächtiger Betrug*.
* Der Auftragsstatus wird nicht geändert, wenn dieselbe Sendung von Admin erstellt wird.

<u>Tatsächliche Ergebnisse</u>:

Bestellstatus = *Verarbeitung*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
