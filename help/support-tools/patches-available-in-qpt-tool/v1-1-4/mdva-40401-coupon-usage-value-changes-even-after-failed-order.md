---
title: "MDVA-40401: Änderung des Verwendungswerts des Gutscheins nach fehlgeschlagener Bestellung"
description: Der Patch MDVA-40401 behebt das Problem, dass sich der Wert der Couponnutzung auch nach einer fehlgeschlagenen Bestellung ändert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40401. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: c497ee84-9c20-4c75-ad3a-3b71f699acbf
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# MDVA-40401: Der Verwendungswert des Gutscheins ändert sich nach fehlgeschlagener Bestellung

Der Patch MDVA-40401 behebt das Problem, dass sich der Wert der Couponnutzung auch nach einer fehlgeschlagenen Bestellung ändert. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 ist installiert. Die Patch-ID lautet MDVA-40401. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzer können den Gutschein nicht erneut anwenden, nachdem sie ihn in einer fehlgeschlagenen Reihenfolge verwendet haben.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Warenkorbregel mit automatisch generierten Gutscheinen.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und wenden Sie den Gutschein an.
1. Navigieren Sie zu **Checkout**.
1. Nehmen Sie das hinzugefügte Produkt &quot;nicht vorrätig&quot;vor, bevor Sie die Bestellung aufgeben.
1. Sie sollten eine *nicht vorrätig* Fehler.
1. Führen Sie cron aus.
1. Gehen Sie zum Warenkorb und entfernen Sie das Produkt.
1. Fügen Sie ein anderes Produkt hinzu und wenden Sie den Gutschein an.

<u>Erwartete Ergebnisse</u>:

Der Gutscheincode sollte erfolgreich angewendet werden, da die vorherige Bestellung nicht platziert wurde.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten eine *Couponcode ist ungültig* Fehler.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungstyp die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
