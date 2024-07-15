---
title: '"MDVA-35092: Vimeo-Fehler: "Video nicht gefunden"'
description: 'Der Patch "MDVA-35092"behebt das Problem, bei dem Fehler angezeigt wird: *"Video nicht gefunden"*. Diese Fehlermeldung wird angezeigt, wenn Sie ein Video über die native Benutzeroberfläche zum Hinzufügen von Videos in der Produktadministratorin von Adobe Commerce eingeben. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde."'
exl-id: bc0952d9-1ea4-417c-926c-96875984d82c
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# MDVA-35092: Vimeo-Fehler: &quot;Video nicht gefunden&quot;

Der Patch MDVA-35092 behebt das Problem, bei dem Fehler angezeigt wird: *&quot;Video nicht gefunden&quot;*. Diese Fehlermeldung wird angezeigt, wenn Sie ein Video über die native Benutzeroberfläche zum Hinzufügen von Videos in der Produktadministratorin von Adobe Commerce eingeben. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce vor Ort und Adobe Commerce über Cloud-Infrastruktur 2.3.5 - 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die einfache Vimeo-API funktioniert nicht mehr wie erwartet.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Administrator an.
1. Um ein vorhandenes Produkt zu bearbeiten, gehen Sie zu **KATALOG** > **Produkte** > **Bearbeiten** oder um ein neues Produkt zu erstellen, gehen Sie zu **KATALOG** > **Produkte** > **Bearbeiten** > **Produkt hinzufügen**.
1. Klicken Sie auf der Produktseite auf die Registerkarte **Bilder und Videos** .
1. Klicken Sie auf **Video hinzufügen** und fügen Sie die URL eines Videos hinzu. Klicken Sie auf **Speichern**.

<u>Erwartete Ergebnisse</u>:

Das neue Video wird gefunden und gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Fehler: *&quot;Video nicht gefunden&quot;* wird angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) verfügbare Patches.
