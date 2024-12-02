---
title: 'MDVA-40401: Der Verwendungswert des Gutscheins ändert sich nach fehlgeschlagener Bestellung'
description: Der Patch MDVA-40401 behebt das Problem, dass sich der Wert der Couponnutzung auch nach einer fehlgeschlagenen Bestellung ändert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40401. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: c497ee84-9c20-4c75-ad3a-3b71f699acbf
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# MDVA-40401: Der Verwendungswert des Gutscheins ändert sich nach fehlgeschlagener Bestellung

Der Patch MDVA-40401 behebt das Problem, dass sich der Wert der Couponnutzung auch nach einer fehlgeschlagenen Bestellung ändert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40401. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzer können den Gutschein nicht erneut anwenden, nachdem sie ihn in einer fehlgeschlagenen Reihenfolge verwendet haben.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Warenkorbregel mit automatisch generierten Gutscheinen.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und wenden Sie den Gutschein an.
1. Wechseln Sie zu **Checkout**.
1. Nehmen Sie das hinzugefügte Produkt &quot;nicht vorrätig&quot;vor, bevor Sie die Bestellung aufgeben.
1. Sie sollten den Fehler *nicht vorrätig* erhalten.
1. Führen Sie cron aus.
1. Gehen Sie zum Warenkorb und entfernen Sie das Produkt.
1. Fügen Sie ein anderes Produkt hinzu und wenden Sie den Gutschein an.

<u>Erwartete Ergebnisse</u>:

Der Gutscheincode sollte erfolgreich angewendet werden, da die vorherige Bestellung nicht platziert wurde.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten den Fehler *Couponcode ist ungültig*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungstyp die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) verfügbare Patches.
