---
title: 'MDVA-38929: Rechnung mit FPT zeigt falsche Summe an'
description: Der MDVA-38929 Patch löst das Problem, dass die Rechnung mit FPT eine falsche Gesamtsumme anzeigt, wenn die Bestellung mit Warenkorb-Guthaben bezahlt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-38929. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
exl-id: 1ed0e311-f4a5-4dc0-98fc-fc1cc9458516
feature: Invoices, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-38929: Rechnung mit FPT zeigt falsche Summe an

Der MDVA-38929 Patch löst das Problem, dass die Rechnung mit FPT eine falsche Gesamtsumme anzeigt, wenn die Bestellung mit Warenkorb-Guthaben bezahlt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-38929. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Rechnung mit FPT zeigt eine falsche Gesamtsumme an, wenn die Bestellung mit Warenkorbguthaben bezahlt wird.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einen Kunden und stellen Sie sicher, dass der Kunde über ausreichend Guthaben verfügt, um die Bestellung abzudecken.
1. Aktivieren von FTP und Hinzufügen von FTP zu einem Produkt.
1. Melden Sie sich vom Frontend aus als der soeben erstellte Kunde an.
1. Fügen Sie das Produkt mit FTP zum Warenkorb hinzu.
1. Checkout und bezahlen mit Ladenkredit. Es sollte ein Nullzahlungsauftrag sein.
1. Gehen Sie zu Bestellungen und fakturieren Sie die Bestellung manuell.
1. Prüfen Sie die Gesamtsumme der Rechnung.

<u>Erwartete Ergebnisse</u>:

* Die Rechnungssumme ist null.
* Der insgesamt gezahlte Bestellbetrag ist null.

<u>Tatsächliche Ergebnisse</u>:

* Die Rechnungssumme zeigt weiterhin den FPT-Betrag an.
* Die insgesamt gezahlte Summe zeigt weiterhin den FPT-Betrag an.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in unserer Entwicklerdokumentation.
