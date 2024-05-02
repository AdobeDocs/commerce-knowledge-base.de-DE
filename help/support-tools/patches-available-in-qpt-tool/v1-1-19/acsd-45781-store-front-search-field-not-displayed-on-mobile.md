---
title: '"ACSD-45781: Suchfeld "Vorderseite speichern"wird nicht auf Mobilgeräten angezeigt'
description: Der Patch MDVA-45781 behebt das Problem, dass das Feld für die Storefront-Suche nicht auf Mobilgeräten angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19 installiert ist. Die Patch-ID lautet MDVA-45781. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: 0ae90f6d-1c04-4599-b21d-4d02fd6b36db
feature: Cache, Native Luma Frontend Development, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-45781: Suchfeld &quot;Vorderseite speichern&quot;wird nicht auf einem Mobilgerät angezeigt

Der Patch MDVA-45781 behebt das Problem, dass das Feld für die Storefront-Suche nicht auf Mobilgeräten angezeigt wird. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) Version 1.1.19 ist installiert. Die Patch-ID lautet MDVA-45781. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.1-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Suchfeld &quot;Vorderseite speichern&quot;wird nicht auf einem Mobilgerät angezeigt

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu Commerce Admin > **Stores** > **Konfiguration** > **Katalog** > **Katalogsuche** und festlegen:
   * Aktivieren Sie Recommendations in *Nein*
   * Suchvorschläge aktivieren auf *Nein*
1. Klicken Sie auf **Konfiguration speichern** Schaltfläche.
1. Cache leeren.
1. Verwenden Sie das standardmäßige Luma-Design und suchen Sie mit Mobilgeräten.
1. Klicken Sie auf **Suche** Schaltfläche.

<u>Erwartete Ergebnisse</u>:

Das Suchformular für die Eingabe wird angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Nichts passiert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
