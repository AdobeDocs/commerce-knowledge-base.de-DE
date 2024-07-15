---
title: "MDVA-42645: Administratoren können keine Bonuspunkte für deaktivierte Store-Gutschriften zurückerstatten."
description: Der Patch MDVA-42645 behebt das Problem, dass der Administrator keine Bonuspunkte zurückgeben kann, wenn die Funktion zum Speichern von Guthaben deaktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42645. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: 8e8f8c07-c1a2-4031-a2fb-cb737165dc2c
feature: Admin Workspace, Orders, Rewards, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-42645: Administratoren können keine Bonuspunkte für deaktivierte Store-Gutschriften zurückerstatten

Der Patch MDVA-42645 behebt das Problem, dass der Administrator keine Bonuspunkte zurückgeben kann, wenn die Funktion zum Speichern von Guthaben deaktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42645. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Administrator kann keine Bonuspunkte zurückgeben, wenn die Funktion zum Speichern von Guthaben deaktiviert ist.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein einfaches Produkt.
1. Erstellen Sie ein neues Kundenkonto und fügen Sie einige Bonuspunkte hinzu.
1. Deaktivieren Sie die Funktion &quot;Kreditspeicher speichern&quot;, indem Sie zu **Store** > Einstellungen > **Konfiguration** > **Kunde** > **Kundenkonfiguration** > **Kreditoptionen speichern** navigieren.
1. Melden Sie sich als Kunde an, dem die Belohnungspunkte zugewiesen sind.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und navigieren Sie zum Checkout.
1. Verwenden Sie die Bonuspunkte im Zahlungsabschnitt und geben Sie die Bestellung auf.
1. Öffnen Sie die Bestellung im Admin und rechnen Sie die Bestellung auf.
1. Klicken Sie auf den Link **Credit Memo** , um ein neues Kreditmemo zu erstellen.
1. Tippen Sie unten auf die Option &quot;Rückerstattungspunkte&quot;und klicken Sie auf die Option **Offline zurückerstatteten**.

<u>Erwartete Ergebnisse</u>:

* Das Credit Memo wurde erfolgreich erstellt.
* Die Belohnungspunkte werden erfolgreich zurückerstattet.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten die folgende Fehlermeldung: *Sie können nicht mehr Speicher-Guthaben als den Bestellbetrag verwenden.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
