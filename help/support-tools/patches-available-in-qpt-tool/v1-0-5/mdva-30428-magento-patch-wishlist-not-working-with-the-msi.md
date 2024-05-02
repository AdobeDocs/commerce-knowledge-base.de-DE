---
title: "MDVA-30428: wishlist not working with Inventory management"
description: Der Patch MDVA-30428 löst die Wunschliste, die nicht mit Inventory management (MSI) funktioniert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 installiert ist.
exl-id: 79e8d5d6-b073-48cf-8ecc-5c44667c12ad
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-30428: Wunschliste funktioniert nicht mit Inventory management

Der Patch MDVA-30428 löst die Wunschliste, die nicht mit Inventory management (MSI) funktioniert. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 ist installiert.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3 - 2.3.3-p1 (QPT 1.0.6) und 2.3.5 - 2.4.1 (QPT 1.0.5)

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn ein Produkt auf die Wunschliste gesetzt wird und das Produkt einer benutzerdefinierten Inventarquelle zugeordnet ist, zeigt die folgende Meldung &quot;*Das Element kann jetzt nicht zur Wunschliste hinzugefügt werden: Es ist nicht möglich, ein Produkt ohne Lager zur Wunschliste hinzuzufügen.*&quot;

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue Lagerbestandsquelle in der Commerce-Admin-Konsole. Eine Anleitung finden Sie unter [Katalog > Hinzufügen einer neuen Quelle](https://docs.magento.com/user-guide/catalog/inventory-sources-add.html?itm_source=merchdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=new%20inventory%20source) in unserem Benutzerhandbuch.
1. Erstellen Sie in Commerce Admin einen neuen Lagerbestand, weisen Sie die neue Quelle und die Standardwebsite dem neuen Lager zu. Eine Anleitung finden Sie unter [Katalog > Neuen Stock hinzufügen](https://docs.magento.com/user-guide/catalog/inventory-stock-add.html#add-new-stock) in unserem Benutzerhandbuch.
1. Erstellen Sie ein einfaches Produkt und weisen Sie den neuen Bestand nur als Bestand zu.
1. Besuchen Sie die Seite mit den einfachen Produktdetails im Frontend.
1. Fügen Sie das Produkt zur Wunschliste hinzu. Der folgende Fehler zeigt: *Das Element kann jetzt nicht zur Wunschliste hinzugefügt werden: Produkt ohne Lager kann nicht zur Wunschliste hinzugefügt werden*.

<u>Erwartete Ergebnisse</u>:

Das Produkt sollte der Wunschliste mit dem benutzerdefinierten Lager hinzugefügt werden.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt wird nicht zur Wunschliste hinzugefügt und es wird eine Fehlermeldung angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
