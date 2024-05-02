---
title: "MDVA-40399: Teilrechnungen für dieselbe Bestellung können nicht gleichzeitig über API erstellt werden"
description: Der Patch MDVA-40399 behebt das Problem, dass Teilrechnungen für die gleiche Bestellung nicht gleichzeitig über die Rest-API erstellt werden können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40399. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: 2444ba57-b30b-4fdf-9e5d-988cf7fa8dd1
feature: REST, Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# MDVA-40399: Teilrechnungen für dieselbe Bestellung können nicht gleichzeitig über API erstellt werden

Der Patch MDVA-40399 behebt das Problem, dass Teilrechnungen für die gleiche Bestellung nicht gleichzeitig über die Rest-API erstellt werden können. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 ist installiert. Die Patch-ID lautet MDVA-40399. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Teilrechnungen für dieselben Bestellungen können nicht gleichzeitig mit der Rest-API erstellt werden.

<u>Voraussetzungen</u>:

Ein konfigurierbares Produkt mit mindestens zwei Varianten.

<u>Zu reproduzierende Schritte</u>:

1. Fügen Sie beide Varianten des konfigurierbaren Produkts zum Warenkorb hinzu.
1. Platzieren Sie die Bestellung.
1. Erstellen Sie zwei Rechnungen gleichzeitig für die Bestellung über die Rest-API.

<u>Erwartete Ergebnisse</u>:

* Beide Rechnungen müssen erfolgreich erstellt werden.
* `qty_invoiced` für beide Rechnungen im `sales_order_item` Tabelle.
* Für beide Produkte sollte eine fakturierte Menge vorliegen.

<u>Tatsächliche Ergebnisse</u>:

* Beide Rechnungen wurden erfolgreich erstellt.
* `qty_invoiced` nicht mit einer der Rechnungen im `sales_order_item` Tabelle.
* Im Admin **Bestellansicht** -Seite, wird die Rechnungsmenge nur für ein Produkt angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
