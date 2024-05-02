---
title: "MDVA-40609: Produktdaten in Kataloginventory_stock_status-Tabelle deaktiviert"
description: Der Patch MDVA-40609 behebt das Problem, dass die Daten zu deaktivierten Produkten nicht in der Indextabelle "cataloginventory_stock_status"angezeigt werden, was zur Anzeige falscher Produktmengen führte. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-40609. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: 2424c3b3-8bc9-4dd4-908c-9d653f09a57a
feature: Catalog Management, Inventory, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-40609: Produktdaten in Kataloginventory_stock_status-Tabelle wurden deaktiviert.

Der Patch MDVA-40609 behebt das Problem, dass die Daten zu deaktivierten Produkten nicht im `cataloginventory_stock_status` Indextabelle, die zu falschen Produktmengen führte. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-40609. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Deaktivierte Produktdaten werden nicht im `cataloginventory_stock_status` Indextabelle, die zu falschen Produktmengen führte.

<u>Voraussetzungen</u>:

Das Lagerbestandsmodul ist installiert.

<u>Zu reproduzierende Schritte</u>:

1. Richten Sie zwei Websites mit Geschäften und Store-Ansichten ein.
1. Erstellen Sie eine zusätzliche Quelle und ein weiteres Lager.
1. Fügen Sie ein einfaches Produkt hinzu:
   * Setzen Sie Produkt aktivieren auf *Nein*.
   * Weisen Sie zwei Quellen mit Quellelementstatus = Vorrätig und Menge größer als null zu.
1. Speichern Sie das Produkt.
1. Überprüfen Sie die **Produktverkaufsmenge** Registerkarte.

<u>Erwartete Ergebnisse</u>:

Beide Bestände haben Werte über null eingegeben.

<u>Tatsächliche Ergebnisse</u>:

Ein Bestand hat einen Nullwert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) Abschnitt.
