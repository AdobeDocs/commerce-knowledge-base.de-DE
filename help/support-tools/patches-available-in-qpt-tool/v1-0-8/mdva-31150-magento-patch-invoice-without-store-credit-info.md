---
title: "MDVA-31150: Rechnung ohne Store-Kreditdaten"
description: Der Patch MDVA-31150 behebt das Problem, dass eine Rechnung ohne Store-Kreditdaten erstellt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.2 behoben wird.
exl-id: 70c87b67-6449-4285-9679-cca81613aa72
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-31150: Rechnung ohne Store-Kreditdaten

Der Patch MDVA-31150 behebt das Problem, dass eine Rechnung ohne Store-Kreditdaten erstellt wird. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.2 behoben wird.

## Betroffene Produkte und Versionen

* Dieser Patch wurde für Adobe Commerce in der Cloud-Infrastruktur 2.3.5-p2 entwickelt.
* Der Patch ist auch mit Adobe Commerce On-Premise und Adobe Commerce in der Cloud-Infrastruktur 2.3.0 bis 2.3.5-p2 und 2.4.0 bis 2.4.0-p1 kompatibel.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nach der Rechnungsstellung durch die API sind die verwendeten Kundendaten und Geschenkkarten nicht in der Rechnung enthalten.

<u>Zu reproduzierende Schritte</u>

1. Hinzufügen eines Store-Guthabenbetrags zu einem Kundenkonto: Gehen Sie in der Admin-Seitenleiste zu **Kunden** > **Alle Kunden.**
1. Kundendatensatz suchen und auf **Bearbeiten** in der Spalte Aktion und **Store-Guthaben** > Saldo aktualisieren > **Kunden speichern**.
1. Gehen Sie zur Storefront und fügen Sie Produkte zum Warenkorb hinzu.
1. Bestellen Sie eine Bestellung, indem Sie den Kreditkartenbetrag oder den Betrag der Geschenkkarte als Teilzahlung anwenden.
1. Erstellen Sie eine Rechnung mithilfe von `REST API>POST>/rest/V1/order/1/invoice` mit Payload:    ```    { "capture": true, "items": [ { "extension_attributes": {}, "order_item_id": 3, "qty": 1 } ], "notify": true, "appendComment": true, "comment": { "extension_attributes": {}, "comment": "string", "is_visible_on_front": 0 }, "arguments": { "extension_attributes": {} }}    ```
1. Abrufen der gerade erstellten Rechnung mit `REST API>GET>/rest/V1/invoices/1`.

<u>Erwartetes Ergebnis</u>

Die Guthaben- und Geschenkkarten-Depots werden per API-Aufruf zurückgegeben.

<u>Tatsächliches Ergebnis</u>

Die Guthaben- und Geschenkkarten-Depots werden nicht per API-Aufruf zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
