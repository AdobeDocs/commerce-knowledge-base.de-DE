---
title: '"MDVA-39195: "Add to Cart is inactive on Category Page"'
description: Der Patch MDVA-39195 behebt das Problem, dass die Schaltfläche "Zum Warenkorb hinzufügen"auf der Kategorieseite inaktiv ist, wenn die Umleitung zum Warenkorb aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39195. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: de434908-e13a-4ab5-abb1-570bcc59c83d
feature: Categories, Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# MDVA-39195: &quot;Zum Warenkorb hinzufügen&quot;ist auf Kategorieseite inaktiv

Der Patch MDVA-39195 behebt das Problem, dass die Schaltfläche **Zum Warenkorb hinzufügen** auf der Kategorieseite inaktiv ist, wenn die Umleitung zum Warenkorb aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39195. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Schaltfläche **Zum Warenkorb hinzufügen** ist auf der Kategorieseite inaktiv, wenn die Umleitung zum Warenkorb aktiviert ist.

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Checkout**.
1. Erweitern Sie den Abschnitt **Warenkorb** .
1. Setzen Sie die **nach dem Hinzufügen einer Produktumleitung zum Warenkorb** auf &quot;Ja&quot;.
1. Besuchen Sie die Seite Kategorie .

<u>Erwartete Ergebnisse</u>:

**Zum Warenkorb hinzufügen** ist auf der Kategorieseite aktiv.

<u>Tatsächliche Ergebnisse</u>:

Die Schaltfläche **Zum Warenkorb hinzufügen** ist auf der Kategorieseite inaktiv.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
