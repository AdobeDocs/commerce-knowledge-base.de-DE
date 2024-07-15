---
title: "MDVA-29787: verwandte Produkte werden nicht angezeigt"
description: Der Patch MDVA-29787 behebt das Problem, dass **Related Products** nicht auf einem Adobe Commerce Store-Frontend angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 installiert ist. Die Patch-ID lautet MDVA-29787.
exl-id: ee060d7b-3b0e-4bd5-84e6-fbd6d2fa532f
feature: Cache, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# MDVA-29787: verwandte Produkte werden nicht angezeigt

Der Patch MDVA-29787 behebt das Problem, dass **Related Products** nicht auf einem Adobe Commerce Store-Frontend angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 installiert ist. Die Patch-ID lautet MDVA-29787.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf Cloud-Infrastruktur 2.3.3.

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.0.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Zielregel für **Zugehörige Produkte** funktioniert nicht, wenn die Bedingung &quot;*ist eine der*&quot;für **Produkte zur Anzeige** in der Commerce-Admin verwendet wird.

>[!NOTE]
>
>Hinweis: Dieser Patch behebt keine vorhandenen Zielregeln. Sie müssen vorhandene Zielregeln neu erstellen.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie **Neues Attribut** (Beispiel: Test\_Attr).
   * Legen Sie **Catalog Input Type für Store Owner** = *Text.* fest.
   * Legen Sie in den **Storefront-Eigenschaften** **Use for Promo Rule Conditions** = *Yes* fest.
1. Erstellen Sie **neuen Attributsatz** (Beispiel: Test\_Set).
1. Fügen Sie das **neue Attribut** zum **neuen Attributsatz** hinzu (Beispiel: Fügen Sie dem Attributsatz &quot;Test\_Set&quot;das Attribut &quot;Test\_Attr&quot;hinzu).
1. Erstellen Sie drei Produkte. Für das Beispiel werden sie wie folgt festgelegt:
   * Product1, Test\_Attr = MAGT2NA\_Test3
   * Product2, Test\_Attr = 24-MB02
   * Produkt3, Test\_Attr = 701644329389M
1. Erstellen der Ziel-Regel **Regel** (**Marketing**)   > **Zugehörige Produktregeln** und klicken Sie auf die Schaltfläche **Regel hinzufügen**.) mit Einstellungen:
   * **Anwenden auf** = *verwandte Produkte*
   * **Entsprechende Produkte**
   * Legen Sie das neue Attribut, das Sie in **** Schritt 1 oben **erstellt haben, auf das Attribut von Produkt1 fest (Beispiel: Test\_Attr = MAGT2NA\_Test3).**
   * **Anzuzeigende Produkte** = Die Attribute der beiden anderen Produkte (Beispiel: Attribute 24-MB02 und 701644329389M).
1. Speichern Sie die **Regel**.
1. Führen Sie bei Bedarf eine Neuindizierung aus.
1. Löschen Sie den Cache.
1. Öffnen Sie Product1 auf der Vorderseite.

<u>Erwartete Ergebnisse</u>:

Die verwandten Produkte sind vorhanden.

<u>Tatsächliche Ergebnisse</u>:

Die verwandten Produkte fehlen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
