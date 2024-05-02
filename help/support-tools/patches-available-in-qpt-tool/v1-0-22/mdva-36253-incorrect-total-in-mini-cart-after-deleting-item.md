---
title: "MDVA-36253: Falsche Gesamtsumme im Mini-Warenkorb nach dem Löschen des Artikels"
description: Der Patch MDVA-36253 behebt das Problem, dass der Produktpreis nicht aktualisiert wird, wenn Sie nach dem Löschen eines Produkts im Schritt zum Auschecken mehrerer Sendungen zur Mini-Warenkorbseite zurückkehren. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 installiert ist. Die Patch-ID lautet MDVA-36253. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: cbd436d7-7fbd-46dd-97cf-30f709da1ce5
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-36253: Falsche Gesamtsumme im Mini-Warenkorb nach dem Löschen des Artikels

Der Patch MDVA-36253 behebt das Problem, dass der Produktpreis nicht aktualisiert wird, wenn Sie nach dem Löschen eines Produkts im Schritt zum Auschecken mehrerer Sendungen zur Mini-Warenkorbseite zurückkehren. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 ist installiert. Die Patch-ID lautet MDVA-36253. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0-2.4.1-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Falsche Gesamtsumme im Mini-Warenkorb nach dem Löschen des Artikels.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich als Kunde an, der über mindestens eine Adresse verfügt.
1. Fügen Sie vier Produkte zum Warenkorb hinzu (Preis = jeweils 10 USD).
1. Gehen Sie zum Warenkorb und klicken Sie auf **Mit mehreren Adressen auschecken**.
1. Entfernen Sie ein Element.
1. Navigieren Sie zurück zur Startseite.
1. Öffnen Sie den Warenkorb und überprüfen Sie den Gesamtpreis.

<u>Erwartete Ergebnisse</u>:

Insgesamt beträgt 30 Dollar.

<u>Tatsächliche Ergebnisse</u>:

Insgesamt sind 40 Dollar.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
