---
title: "MDVA-32632: Bestellungen im Zahlungssystem, aber nicht in Adobe Commerce"
description: Die MDVA-32632 löst die Frage, ob Bestellungen in einem Zahlungssystem, aber nicht in Adobe Commerce getätigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.3.5 behoben wurde.
exl-id: f9b2fee4-9905-47cb-a71a-121426e93beb
feature: Orders, Payments, System
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# MDVA-32632: Bestellungen im Zahlungssystem, aber nicht in Adobe Commerce

Die MDVA-32632 löst die Frage, ob Bestellungen in einem Zahlungssystem, aber nicht in Adobe Commerce getätigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.3.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.2-p2

**Der Patch ist auch mit der Adobe Commerce-Version kompatibel:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.2 - 2.3.4-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Zahlung erfolgt in einem Zahlungssystem, die Bestellung wird jedoch nicht in Adobe Commerce erstellt.

<u>Zu reproduzierende Schritte</u>:

1. Bestellung mittels Online-Zahlungsmethode.
1. Überprüfen Sie die Bestellung in Commerce Admin.

<u>Erwartete Ergebnisse</u>:

Abgeschlossene Bestellungen werden jetzt im Zahlungssystem und in Adobe Commerce angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die Bestellungen wurden erfolgreich vom Zahlungssystem verarbeitet, nicht jedoch in Adobe Commerce.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie in der [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
