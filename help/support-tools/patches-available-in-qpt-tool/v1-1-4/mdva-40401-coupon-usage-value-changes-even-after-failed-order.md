---
title: 'MDVA-40401: Änderungen des Couponnutzungswerts nach fehlgeschlagener Bestellung'
description: Der Patch MDVA-40401 behebt das Problem, dass sich der Couponnutzungswert auch nach einer fehlgeschlagenen Bestellung ändert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40401. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
exl-id: c497ee84-9c20-4c75-ad3a-3b71f699acbf
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# MDVA-40401: Änderungen des Couponnutzungswerts nach fehlgeschlagener Bestellung

Der Patch MDVA-40401 behebt das Problem, dass sich der Couponnutzungswert auch nach einer fehlgeschlagenen Bestellung ändert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40401. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzer können den Coupon nicht erneut anwenden, nachdem sie ihn in einer fehlgeschlagenen Reihenfolge verwendet haben.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Warenkorbregel mit automatisch generierten Coupons.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und wenden Sie den Gutschein an.
1. Navigieren Sie zu **Checkout**.
1. Machen Sie das hinzugefügte Produkt „nicht vorrätig“, bevor Sie die Bestellung aufgeben.
1. Es sollte ein Fehler *Nicht vorrätig* ausgegeben werden.
1. Cron ausführen.
1. Gehen Sie zum Warenkorb und entfernen Sie das Produkt.
1. Fügen Sie ein weiteres Produkt hinzu und wenden Sie den Gutschein an.

<u>Erwartete Ergebnisse</u>:

Der Gutscheincode sollte erfolgreich angewendet werden, da die vorherige Bestellung nicht aufgegeben wurde.

<u>Tatsächliche Ergebnisse</u>:

Es wird ein Fehler *Gutscheincode ist ungültig* ausgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungstyp die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
