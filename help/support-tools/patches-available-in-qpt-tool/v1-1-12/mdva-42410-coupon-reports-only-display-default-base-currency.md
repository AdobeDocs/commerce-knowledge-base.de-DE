---
title: "MDVA-42410: Gutscheinberichte zeigen nur die Standardgrundwährung an"
description: Der Patch MDVA-42410 behebt das Problem, dass die Gutscheinberichte nur die Basiswährung anzeigen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42410. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: b442a2ce-1bd4-4f09-95fd-2c626e32f509
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-42410: Gutscheinberichte zeigen nur die Standardgrundwährung an

Der Patch MDVA-42410 behebt das Problem, dass die Gutscheinberichte nur die Basiswährung anzeigen. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42410. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Gutscheinberichte zeigen nur die Standardgrundwährung an.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine zusätzliche Website-, Store- und Store-Ansicht.
1. Legen Sie für diese neue Website eine andere Währung fest. Beispiel: Euro.
1. Navigieren Sie zu **Stores** > **Wechselkurse** und konfigurieren Sie die Währungssätze in **Euro**.
1. Erstellen Sie eine **Preisregel für Warenkorb** mit einem bestimmten Gutschein - **Test**.
1. Gehen Sie zum Frontend und geben Sie eine Bestellung mit der **Test** Gutschein auf der neuen Website.
1. Navigieren Sie zu **Berichte** > **Vertrieb** > **Coupons**.
1. Wählen Sie die neue Website im Dropdown-Menü Umfang aus.
1. Aktualisieren Sie Statistiken und führen Sie Berichte aus.

<u>Erwartete Ergebnisse</u>:

Gutscheinberichte zeigen die Währung der neuen Website als Euro an.

<u>Tatsächliche Ergebnisse</u>:

Die Standardgrundwährung (in diesem Fall USD) wird in Gutscheinberichten für die neue Website verwendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
