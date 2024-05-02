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

Der Patch MDVA-29787 löst das Problem, bei dem **Verwandte Produkte** werden nicht auf einem Adobe Commerce Store-Frontend angezeigt. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 installiert ist. Die Patch-ID lautet MDVA-29787.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf Cloud-Infrastruktur 2.3.3.

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.0.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Zielregel für **Verwandte Produkte** funktioniert nicht, wenn *ist einer von*&quot; wird verwendet für **Angezeigte Produkte** in der Commerce-Admin.

>[!NOTE]
>
>Hinweis: Dieser Patch behebt keine vorhandenen Zielregeln. Sie müssen vorhandene Zielregeln neu erstellen.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen **Neues Attribut** (Beispiel: Test\_Attr).
   * Satz **Katalogeingabetyp für Store Owner** = *Text.*
   * In **Store-Eigenschaften**, set **Verwendung für Bedingungen für Angebotsregeln** = *Ja*.
1. Erstellen **Neuer Attributsatz** (Beispiel: Test\_Set).
1. Fügen Sie die **Neues Attribut** der **Neuer Attributsatz** (Beispiel: Fügen Sie dem Attributsatz &quot;Test\_Set&quot;das Attribut &quot;Test\_Attr&quot;hinzu.)
1. Erstellen Sie drei Produkte. Für das Beispiel werden sie wie folgt festgelegt:
   * Product1, Test\_Attr = MAGT2NA\_Test3
   * Product2, Test\_Attr = 24-MB02
   * Produkt3, Test\_Attr = 701644329389M
1. Ziel erstellen **Regel** (**Marketing**   > **Verwandte Produktregeln** und klicken Sie auf **Regel hinzufügen** Schaltfläche.) mit Einstellungen:
   * **Anwenden auf** = *Verwandte Produkte*
   * **Zu vergleichende Produkte**
   * Festlegen des von Ihnen erstellten neuen Attributs **in** **Schritt 1 oben** als Attribut von Produkt1 verwenden (Beispiel: Test\_Attr = MAGT2NA\_Test3).
   * **Angezeigte Produkte** = Die Attribute der beiden anderen Produkte (Beispiel: Attribute 24-MB02 und 701644329389M).
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

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
