---
title: "MDVA-32545 Patch: Bestellrechnungen werden nicht automatisch gesendet"
description: Der Patch MDVA-32545 behebt das Problem, dass Invoice-E-Mails nicht automatisch an den Kunden gesendet werden, um Bestellungen vom Administrator zu erhalten. Dies wirkt sich auf jede Zahlungsmethode mit dem Typ "Verkauf"aus, z. B. **Braintree** oder **PayPal Payflow Pro**.
exl-id: 682eaeb1-5475-4d37-9536-0605f5b9f163
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# MDVA-32545 Patch: Bestellrechnungen werden nicht automatisch gesendet

Der Patch MDVA-32545 behebt das Problem, dass Invoice-E-Mails nicht automatisch an den Kunden gesendet werden, um Bestellungen vom Administrator zu erhalten. Dies wirkt sich auf jede Zahlungsmethode mit dem Transaktionstyp **Verkauf** aus, z. B. **Braintree** oder **PayPal Payflow Pro**.

Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.0 - 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie jede Zahlungsmethode mit dem Transaktionstyp **Verkauf** . (Beispiel: **Braintree** oder **PayPal Payflow Pro**.)
1. Erstellen Sie ein einfaches Produkt.
1. Erstellen Sie ein Kundenkonto im Frontend.
1. Platzieren Sie eine Bestellung beim Administrator.

<u>Erwartete Ergebnisse</u>:

Die E-Mail zur Rechnungsstellung wird wie erwartet automatisch an den Kunden gesendet.

<u>Tatsächliche Ergebnisse</u>:

Die Rechnungsemail wird nicht automatisch an den Kunden gesendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie in der [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
