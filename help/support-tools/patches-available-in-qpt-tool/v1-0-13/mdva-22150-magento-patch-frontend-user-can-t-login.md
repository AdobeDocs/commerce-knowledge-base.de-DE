---
title: "MDVA-22150 Adobe Commerce Patch: Frontend-Anwender kann sich nicht anmelden"
description: Der Patch MDVA-22150 behebt das Problem, dass sich ein Frontend-Benutzer nach einem abgebrochenen Kauf mit einem Coupon nicht anmelden kann. Dies tritt auf, wenn ein Frontend-Benutzer einen Gutscheincode für ein Produkt verwendet, das vor Abschluss des Kaufs deaktiviert wurde. Dadurch kann sich der Frontend-Benutzer nicht mehr anmelden und erhält einen 503-Fehler. Ein weiterer Effekt dieses Problems ist, dass die Möglichkeit, die Warenkorb von Kunden in der Admin-Konsole zu verwalten, nicht mehr funktioniert.
exl-id: 8aabe7b2-4b8a-4339-914e-7131006907b3
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# MDVA-22150 Adobe Commerce Patch: Frontend-Benutzer kann sich nicht anmelden

Der Patch MDVA-22150 behebt das Problem, dass sich ein Frontend-Benutzer nach einem abgebrochenen Kauf mit einem Coupon nicht anmelden kann. Dies tritt auf, wenn ein Frontend-Benutzer einen Gutscheincode für ein Produkt verwendet, das vor Abschluss des Kaufs deaktiviert wurde. Dadurch kann sich der Frontend-Benutzer nicht mehr anmelden und erhält einen 503-Fehler. Ein weiterer Effekt dieses Problems ist, dass die Möglichkeit, die Warenkorb von Kunden in der Admin-Konsole zu verwalten, nicht mehr funktioniert.

Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.3.4 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce in der Cloud-Infrastruktur 2.3.2

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce in der Cloud-Infrastruktur und Adobe Commerce 2.3.1 - 2.3.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte:</u>

1. Melden Sie sich bei Admin an und erstellen Sie ein konfigurierbares Produkt.
1. Gehen Sie zu **Warenkorbregeln** und erstellen Sie einen Gutscheincode mit einem gewissen Rabatt.
1. Erstellen Sie ein Kundenkonto im Frontend.
1. Fügen Sie das Produkt zum Warenkorb hinzu, befolgen Sie den Checkout-Prozess und geben Sie den Gutschein ein.
1. Senden Sie nach Eingabe des Gutscheins nicht die Bestellung, sondern brechen Sie die Bestellung ab und melden Sie sich ab.
1. Gehen Sie zurück zum Admin und deaktivieren Sie das gesamte konfigurierbare Produkt.

<u>Erwartete Ergebnisse:</u>

Das Produkt wird nicht im Warenkorb auf der Storefront angezeigt oder mit der entsprechenden Fehlermeldung angezeigt, dass das Produkt wie erwartet deaktiviert wurde.

<u>Tatsächliche Ergebnisse:</u>

* Beim Versuch, sich wieder in das Frontend einzuloggen, bleiben Sie in einer Endlosschleife stecken (die nach langer Zeit eine Ausnahme anzeigt).
* Die Möglichkeit, die Warenkörbe der Kunden in der Admin-Konsole zu verwalten, funktioniert nicht mehr.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) verfügbare Patches.
