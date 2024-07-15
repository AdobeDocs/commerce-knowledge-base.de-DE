---
title: "MDVA-31295: Treuepunkte bei Teilbestellungen"
description: Der Patch MDVA-31295 behebt das Problem, dass die Belohnungspunkte nicht korrekt berechnet werden, wenn eine partielle Bestellung abgeschlossen und Artikel besteuert werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
exl-id: 10e8a3a9-bfab-4256-b772-fd64e8885da3
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-31295: Treuepunkte bei Teilbestellungen

Der Patch MDVA-31295 behebt das Problem, dass die Belohnungspunkte nicht korrekt berechnet werden, wenn eine partielle Bestellung abgeschlossen und Artikel besteuert werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce vor Ort 2.3.0

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Belohnungen werden nicht auf die Konten der Kunden angewendet, wenn die Bestellung abgeschlossen (teilweise versandt) und Artikel besteuert werden. Wenn die Artikel nicht besteuert werden, werden die Belohnungen den Konten der Kunden erfolgreich hinzugefügt.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei der Storefront als Kunde an.
1. Fügen Sie zwei Produkte zum Warenkorb hinzu.
1. Gehen Sie zum Checkout, legen Sie die Lieferadresse fest, die Steuern hat, und geben Sie die Bestellung auf.
1. Gehen Sie im Admin zur kürzlich aufgegebenen Bestellung.
1. Klicken Sie auf **Rechnung** und setzen Sie **Menge auf Rechnung** für eines der Elemente auf 0 und klicken Sie auf **Menge aktualisieren**. Übermitteln Sie die Rechnung.
1. Klicken Sie auf Senden und setzen Sie **Qty auf Ship** für das Element, das nicht in Rechnung gestellt wurde, auf 0. Klicken Sie auf **Sendung übermitteln**.
1. Klicken Sie auf Abbrechen der Bestellung. Der Status wird auf &quot;Fertig gestellt&quot;festgelegt.
1. Wechseln Sie im Admin zu **Kunden** > Kundenkauf wählen, der vor > **Prämienpunkte** > **Prämienpunktverlauf** getätigt wurde.
1. Überprüfen Sie die verdienten Belohnungspunkte für die platzierte Bestellung.

<u>Erwartete Ergebnisse</u>:

Die Belohnungspunkte sollten für steuerpflichtige Aufträge berechnet werden, wenn eine Teilbestellung abgeschlossen ist.

<u>Tatsächliche Ergebnisse</u>:

Für einen steuerpflichtigen Auftrag werden keine Belohnungspunkte berechnet, wenn eine Teilbestellung abgeschlossen ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
