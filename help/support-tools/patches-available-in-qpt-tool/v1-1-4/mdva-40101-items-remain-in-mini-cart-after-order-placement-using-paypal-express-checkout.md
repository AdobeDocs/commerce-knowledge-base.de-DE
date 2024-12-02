---
title: 'MDVA-40101: Artikel bleiben Mini-Warenkorb nach der Bestellung PayPal Express Checkout'
description: Der Patch MDVA-40101 behebt das Problem, dass Artikel nach einer erfolgreichen Bestellplatzierung mit PayPal Express Checkout nicht aus dem Mini-Warenkorb entfernt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40101. Beachten Sie, dass das Problem in Adobe Commerce 2.4.0 behoben wurde.
exl-id: d640dfcd-6fb6-4cc6-8817-3ae19aa59bed
feature: Checkout, Orders, Payments, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-40101: Artikel bleiben Mini-Warenkorb nach der Bestellung PayPal Express Checkout

Der Patch MDVA-40101 behebt das Problem, dass Artikel nach einer erfolgreichen Bestellplatzierung mit PayPal Express Checkout nicht aus dem Mini-Warenkorb entfernt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40101. Beachten Sie, dass das Problem in Adobe Commerce 2.4.0 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.2 - 2.3.7-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Artikel bleiben auch nach erfolgreicher Bestellplatzierung mit PayPal Express Checkout im Mini-Warenkorb.

<u>Zu reproduzierende Schritte</u>:

Platzieren Sie eine Bestellung mit PayPal Express Checkout im Inkognito-Modus in einem Browser.

<u>Erwartete Ergebnisse</u>:

Der Mini-Warenkorb sollte nach erfolgreichem Abschluss der Bestellung leer sein.

<u>Tatsächliche Ergebnisse</u>:

* Auf der Erfolgsseite wird ein leerer Mini-Warenkorb angezeigt.
* Alle anderen Seiten zeigen einen Mini-Warenkorb mit gekauften Artikeln.
* Durch Klicken auf den Link zum Warenkorb gelangen Sie zu einer leeren Warenkorbseite.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) verfügbare Patches.
