---
title: "MDVA-26639: Keine Bestelleinträge in der neuen E-Mail-Vorlage zur Bestellbestätigung"
description: Der Patch MDVA-26639 behebt das Problem, wenn eine neue Bestellung erstellt wird und die Bestellelemente in einer Bestätigungs-E-Mail-Vorlage fehlen.
exl-id: 5d9716ab-6e57-47b0-8b38-ca98a98101e8
feature: Communications, Marketing Tools, Native Luma Frontend Development, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# MDVA-26639: Keine Bestellelemente in der neuen E-Mail-Vorlage zur Bestellbestätigung

Der Patch MDVA-26639 behebt das Problem, wenn eine neue Bestellung erstellt wird und die Bestellelemente in einer Bestätigungs-E-Mail-Vorlage fehlen.

Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 installiert ist. Die Patch-ID lautet MDVA-26639. Beachten Sie, dass das Problem in Adobe Commerce 2.3.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce für die Cloud-Infrastruktur 2.3.3-p1

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce On-Premise und Adobe Commerce in der Cloud-Infrastruktur 2.3.3-p1-2.3.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu **Stores** > **Konfiguration** > **Verkauf** > **Verkaufs-E-Mails** > **Neue Bestellbestätigung** und wählen Sie **Vorlage: Neue Abholbestellung**.
1. Wechseln Sie zu **Verkauf** > **Bestellung: Wählen Sie eine Bestellung** aus, gehen Sie zu **Informationen** und wählen Sie **E-Mail senden** aus.

<u>Erwartete Ergebnisse</u>:

Die Bestellelemente werden wie erwartet in der E-Mail zur Kundenbestellung angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die Bestellelemente fehlen in der E-Mail zur Kundenbestellung. Dasselbe gilt, wenn Sie eine neue Vorlage erstellen und eine Vorlage für eine neue Bestellung oder eine neue Bestellung (Luma) auswählen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) verfügbare Patches.
