---
title: "MDVA-40175: Optionsfelder werden bei Neuanordnung nicht angezeigt."
description: Der Patch MDVA-40175 löst das Problem, dass die Optionsfelder nicht angezeigt werden, wenn Benutzer versuchen, eine Neuanordnung vorzunehmen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-40175. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: 307c450d-9f53-40b7-b2f5-d867850c043a
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-40175: Optionsfelder werden bei Neuanordnung nicht angezeigt

Der Patch MDVA-40175 löst das Problem, dass die Optionsfelder nicht angezeigt werden, wenn Benutzer versuchen, eine Neuanordnung vorzunehmen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-40175. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Optionsfelder werden nicht im Bereich Zahlungs- und Versandinformationen angezeigt, wenn Benutzer versuchen, eine Neuanordnung vorzunehmen.

<u>Voraussetzungen</u>:

1. Ein Kundenkonto mit einer Lieferadresse und einer Rechnungsadresse wird erstellt.
1. Ein einfaches Produkt wird erstellt.
1. Verschiedene Versandmethoden sind konfiguriert.
1. Es wird mindestens eine Bestellung erstellt.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zum Admin-Bedienfeld > **Verkauf** > **Bestellungen**.
1. Wählen Sie die erstellte Reihenfolge aus.
1. Klicken Sie auf den Link **Anzeigen** .
1. Klicken Sie auf die Schaltfläche **Neu anordnen** .
1. Scrollen Sie auf der Seite nach unten zum Abschnitt **Zahlungs- und Versandinformationen** .
1. Klicken Sie auf **Klicken, um die Versandmethode zu ändern**.

<u>Erwartete Ergebnisse</u>:

Die Liste der Versandmethoden mit Optionsfeldern wird angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die Liste der Versandmethoden ohne Optionsfelder wird angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
