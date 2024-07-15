---
title: '"MDVA-33344 Patch: "rma-item" attribute set ID hard coded"'
description: Der Patch MDVA-33344 behebt das Problem, bei dem die hartcodierte Entitäts-Standardattributset-ID "rma\_item"anstelle des Werts aus der Datenbank verwendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 installiert ist. Bitte beachten Sie, dass das Problem behoben wurde/voraussichtlich in Adobe Commerce 2.4.3 behoben sein wird.
exl-id: 2ef894a3-eea0-4f9f-8d26-984cd408458c
feature: Attributes, B2B
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# MDVA-33344 Patch: &quot;rma-item&quot;-Attributsatz ID hartcodiert

Der Patch MDVA-33344 behebt das Problem, bei dem die hartcodierte Entitäts-Standardattributset-ID &quot;rma\_item&quot;anstelle des Werts aus der Datenbank verwendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 installiert ist. Bitte beachten Sie, dass das Problem behoben wurde/voraussichtlich in Adobe Commerce 2.4.3 behoben sein wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce in der Cloud-Infrastruktur 2.3.4

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce für Cloud-Infrastruktur und Adobe Commerce On-Premise 2.3.0 - 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der WebAPI-Endpunkt `/rest/default/V1/returnsAttributeMetadata` gibt ein leeres Ergebnis zurück, wenn sich die standardmäßige Attributset-ID der Entität &quot;rma\_item&quot;von der standardmäßigen Installations-ID unterscheidet.

<u>Zu reproduzierende Schritte</u>:

Führen Sie einen API-Aufruf an `/rest/default/V1/returnsAttributeMetadata` durch.

<u>Erwartetes Ergebnis</u>:

Daten werden zurückgegeben.

<u>Tatsächliches Ergebnis</u>:

Leeres Ergebnis wird zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie in der [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
