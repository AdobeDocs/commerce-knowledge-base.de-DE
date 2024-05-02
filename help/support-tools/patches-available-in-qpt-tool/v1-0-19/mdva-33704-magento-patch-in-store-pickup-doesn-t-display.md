---
title: "MDVA-33704 Patch: In-store pickup wird nicht angezeigt"
description: Der Patch MDVA-33704 behebt das Problem, dass Produkte mit der Option zur Abholung im Geschäft nicht als Versandmethode angezeigt werden.
exl-id: 2c5c7627-5d2e-44d2-9579-314dbd31ee8b
feature: Shipping/Delivery
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Patch MDVA-33704: In-store pickup zeigt nicht an

Der Patch MDVA-33704 behebt das Problem, dass Produkte mit der Option zur Abholung im Geschäft nicht als Versandmethode angezeigt werden.

Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 ist installiert. Die Patch-ID lautet MDVA-33704. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce auf Cloud-Infrastruktur 2.4.0-p1

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce vor Ort und Adobe Commerce über Cloud-Infrastruktur 2.4.0-2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Voraussetzung</u>:<br>

**Auswählen im Store** enabled

<u>Zu reproduzierende Schritte</u>:

1. Fügen Sie dem Warenkorb ein Produkt hinzu.
1. Wechseln Sie zur Kasse.
1. Fügen Sie Versandinformationen hinzu und wählen Sie eine andere Versandmethode als die In-Store-Abholung.
1. Auswählen **Zahlungsvorgang**, aber gehen Sie dann nicht zur Zahlungsseite.
1. Gehen Sie stattdessen zurück zum **Kontakt und Versand** Abschnitt.
1. Auswählen **Abholen**.
1. Auswählen **Store** und **Klicken auf Zahlung**.
1. Beachten Sie, dass Ihre Lieferadresse automatisch als Rechnungsadresse angegeben wird.
1. Aktualisieren Sie die Webseite.

<u>Erwartete Ergebnisse</u>:

Die Option &quot;In-store-Abholung&quot;wird wie erwartet als Versandmethode angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die Option &quot;In-Store-Abholung&quot;wird nicht als Versandmethode angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
