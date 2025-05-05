---
title: 'MDVA-40399: Teilrechnungen für dieselbe Bestellung können nicht gleichzeitig über API erstellt werden'
description: Der Patch MDVA-40399 behebt das Problem, dass Teilrechnungen für dieselbe Bestellung nicht gleichzeitig über die REST-API erstellt werden können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40399. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
exl-id: 2444ba57-b30b-4fdf-9e5d-988cf7fa8dd1
feature: REST, Invoices, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# MDVA-40399: Teilrechnungen für dieselbe Bestellung können nicht gleichzeitig über API erstellt werden

Der Patch MDVA-40399 behebt das Problem, dass Teilrechnungen für dieselbe Bestellung nicht gleichzeitig über die REST-API erstellt werden können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40399. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Teilrechnungen für dieselben Bestellungen können nicht gleichzeitig mit der REST-API erstellt werden.

<u>Voraussetzungen</u>:

Ein konfigurierbares Produkt mit mindestens zwei Varianten.

<u>Schritte zur Reproduktion</u>:

1. Fügen Sie beide Varianten des konfigurierbaren Produkts zum Warenkorb hinzu.
1. Bestellung aufgeben.
1. Erstellen Sie über die REST-API zwei Rechnungen gleichzeitig für die Bestellung.

<u>Erwartete Ergebnisse</u>:

* Beide Rechnungen müssen erfolgreich erstellt werden.
* `qty_invoiced` sollten für beide Rechnungen in der `sales_order_item` aktualisiert werden.
* Beide Produkte sollten über die fakturierte Menge verfügen.

<u>Tatsächliche Ergebnisse</u>:

* Beide Rechnungen wurden erfolgreich erstellt.
* `qty_invoiced` wird nicht für eine der Rechnungen in der `sales_order_item` aktualisiert.
* Auf der Admin-Seite **Auftragsansicht** wird die Rechnungsmenge nur für ein Produkt angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
