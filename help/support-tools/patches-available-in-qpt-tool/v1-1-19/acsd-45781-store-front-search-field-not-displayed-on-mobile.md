---
title: 'ACSD-45781: Suchfeld "Vorderseite speichern"wird nicht auf einem Mobilgerät angezeigt'
description: Der Patch MDVA-45781 behebt das Problem, dass das Feld für die Storefront-Suche nicht auf Mobilgeräten angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19 installiert ist. Die Patch-ID lautet MDVA-45781. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: 0ae90f6d-1c04-4599-b21d-4d02fd6b36db
feature: Cache, Native Luma Frontend Development, Search
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-45781: Suchfeld &quot;Vorderseite speichern&quot;wird nicht auf einem Mobilgerät angezeigt

Der Patch MDVA-45781 behebt das Problem, dass das Feld für die Storefront-Suche nicht auf Mobilgeräten angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19 installiert ist. Die Patch-ID lautet MDVA-45781. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.1-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Suchfeld &quot;Vorderseite speichern&quot;wird nicht auf einem Mobilgerät angezeigt

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu Commerce Admin > **Stores** > **Konfiguration** > **Katalog** > **Katalogsuche** und legen Sie Folgendes fest:
   * Aktivieren Sie Search Recommendations auf *Nein* .
   * Suchvorschläge aktivieren auf *Nein*
1. Klicken Sie auf die Schaltfläche **Konfiguration speichern** .
1. Cache leeren.
1. Verwenden Sie das standardmäßige Luma-Design und suchen Sie mit Mobilgeräten.
1. Klicken Sie auf die Schaltfläche **Suchen** .

<u>Erwartete Ergebnisse</u>:

Das Suchformular für die Eingabe wird angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Nichts passiert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbar sind, in unserer Entwicklerdokumentation.
