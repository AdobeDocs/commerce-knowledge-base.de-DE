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

Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 ist installiert. Die Patch-ID lautet MDVA-26639. Beachten Sie, dass das Problem in Adobe Commerce 2.3.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce auf Cloud-Infrastruktur 2.3.3-p1

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce vor Ort und Adobe Commerce über Cloud-Infrastruktur 2.3.3-p1-2.3.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **Stores** > **Konfiguration** > **Vertrieb** > **Verkaufs-E-Mails** > **Neue Bestellbestätigung** und wählen **Vorlage: Neue Nachbestellung**.
1. Navigieren Sie zu **Vertrieb** > **Reihenfolge: Wählen Sie eine Bestellung aus**, gehen Sie dann zu **Informationen** und wählen Sie **Send Mail**.

<u>Erwartete Ergebnisse</u>:

Die Bestellelemente werden wie erwartet in der E-Mail zur Kundenbestellung angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die Bestellelemente fehlen in der E-Mail zur Kundenbestellung. Dasselbe gilt, wenn Sie eine neue Vorlage erstellen und eine Vorlage für eine neue Bestellung oder eine neue Bestellung (Luma) auswählen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) Abschnitt.
