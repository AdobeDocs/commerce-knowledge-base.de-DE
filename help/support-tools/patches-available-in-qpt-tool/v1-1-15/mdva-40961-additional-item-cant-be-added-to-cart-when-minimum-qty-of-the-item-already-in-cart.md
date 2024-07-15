---
title: "MDVA-40961: Zusätzlicher Artikel kann nicht zum Warenkorb hinzugefügt werden, wenn die Mindestmenge des Artikels bereits im Warenkorb ist"
description: Der Patch MDVA-40961 behebt das Problem, dass ein zusätzlicher Artikel nicht zum Warenkorb hinzugefügt werden kann, wenn die Mindestmenge des Artikels bereits im Warenkorb ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-40961. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: fc90c2b6-f631-49ff-81b0-e41918dd79a7
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-40961: Zusätzlicher Artikel kann nicht zum Warenkorb hinzugefügt werden, wenn die Mindestmenge des Artikels bereits im Warenkorb ist

Der Patch MDVA-40961 behebt das Problem, dass ein zusätzlicher Artikel nicht zum Warenkorb hinzugefügt werden kann, wenn die Mindestmenge des Artikels bereits im Warenkorb ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-40961. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein weiterer Artikel kann nicht zum Warenkorb hinzugefügt werden, wenn die Mindestmenge des Artikels bereits im Warenkorb ist.

<u>Zu reproduzierende Schritte</u>:

1. Legen Sie für ein einfaches Produkt fest, dass im Warenkorb mehr als eine **Mindestmenge zulässig ist (z. B. zwei).**
1. Öffnen Sie das Produkt in der Storefront und fügen Sie zwei davon zum Warenkorb hinzu.
1. Bleiben Sie auf der Produktseite und fügen Sie ein weiteres Produkt zum Warenkorb hinzu.

<u>Erwartete Ergebnisse</u>:

Das dritte Produkt kann dem Warenkorb hinzugefügt werden, da es bereits den Mindestbetrag enthält.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten die folgende Fehlermeldung: *Die geringste Kaufoption ist 2*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
