---
title: "MDVA-38929: Rechnung mit FPT zeigt falsche Summe an"
description: Der Patch MDVA-38929 löst das Problem, dass die Rechnung mit FPT einen falschen Gesamtwert anzeigt, wenn die Bestellung mit einem Store-Guthaben beglichen wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-38929. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: 1ed0e311-f4a5-4dc0-98fc-fc1cc9458516
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-38929: Rechnung mit FPT zeigt falsche Summe an

Der Patch MDVA-38929 löst das Problem, dass die Rechnung mit FPT einen falschen Gesamtwert anzeigt, wenn die Bestellung mit einem Store-Guthaben beglichen wird. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 ist installiert. Die Patch-ID lautet MDVA-38929. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Rechnung mit FPT zeigt einen falschen Gesamtwert an, wenn die Bestellung mit einem Store-Guthaben bezahlt wird.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen Kunden und stellen Sie sicher, dass der Kunde über ausreichend Guthaben verfügt, um die Bestellung abzudecken.
1. Aktivieren Sie FPT und fügen Sie einem Produkt FPT hinzu.
1. Melden Sie sich vom Frontend an, wie der Kunde gerade erstellt hat.
1. Fügen Sie das Produkt mit FPT zum Warenkorb hinzu.
1. Checkout und bezahlen mit Gutschrift. Es sollte sich um einen Nulllohnauftrag handeln.
1. Gehen Sie zu Bestellungen und berechnen Sie die Bestellung manuell.
1. Überprüfen Sie die Rechnungsgesamtsumme.

<u>Erwartete Ergebnisse</u>:

* Die Rechnungsgesamtsumme ist null.
* Der bezahlte Bestellgesamtbetrag ist null.

<u>Tatsächliche Ergebnisse</u>:

* Die Rechnungsgesamtsumme zeigt weiterhin den FPT-Betrag an.
* Der gezahlte Gesamtbetrag zeigt weiterhin den FPT-Betrag an.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
