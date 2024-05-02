---
title: "MDVA-34928: Checkout-Seitenfehler nach Entfernung des Store-Guthabens"
description: Der Patch MDVA-34928 behebt das Problem, dass nach dem Entfernen von Store-Guthaben ein unendlicher Lader auf der Checkout-Seite vorhanden ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 installiert ist. Die Patch-ID lautet MDVA-34928. Beachten Sie, dass das Problem in Adobe Commerce 2.3.6 behoben wurde.
exl-id: 9ef6777a-88c8-4fed-a296-0cb4e6ad153a
feature: Checkout, Orders, Returns, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-34928: Checkout-Seitenfehler nach entferntem Store-Guthaben

Der Patch MDVA-34928 behebt das Problem, dass nach dem Entfernen von Store-Guthaben ein unendlicher Lader auf der Checkout-Seite vorhanden ist. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 ist installiert. Die Patch-ID lautet MDVA-34928. Beachten Sie, dass das Problem in Adobe Commerce 2.3.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce On-Premise und Adobe Commerce über Cloud-Infrastruktur 2.3.5 - 2.3.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nach dem Entfernen des Store-Guthabens befindet sich auf der Checkout-Seite ein unendlicher Lader.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Kundenkonto.
1. Bestimmen Sie einen möglichen Artikel, der zum Warenkorb hinzugefügt werden kann - beachten Sie den Preis.
1. Bearbeiten Sie das Konto im Admin.
1. Klicks **Store-Guthaben**.
1. Fügen Sie einen Betrag hinzu, um den Preis des Artikels zu decken.
1. Melden Sie sich als Kunde an der Storefront an.
1. Fügen Sie den Artikel zum Warenkorb hinzu.
1. Fahren Sie mit dem Checkout fort.
1. Wenden Sie die Gutschrift für den Store an.
1. Versuchen Sie, das Geschäft-Guthaben zu entfernen.

<u>Erwartete Ergebnisse</u>:

Die Gutschrift für den Store wurde entfernt.

<u>Tatsächliche Ergebnisse</u>:

Unendliche Ladefunktion wird ausgelöst, bis die Seite aktualisiert wird.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
