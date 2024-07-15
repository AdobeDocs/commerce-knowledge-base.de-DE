---
title: "MDVA-32449: Auftragsverlauf ist langsam oder wird mit Fehler 503 nicht geladen"
description: Der Patch MDVA-32449 behebt das Problem in Adobe Commerce, bei dem der Auftragsverlauf langsam lädt oder nicht lädt und ein 503-Fehler angezeigt wird. Dies ist ein Problem, bei dem 13000+ Kunden einem B2B-Unternehmen zugewiesen werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 installiert ist. Bitte beachten Sie, dass dieses Problem in Adobe Commerce 2.4.1 behoben wurde.
exl-id: e3fd4db2-b706-4712-ba8e-270eaca7fdb2
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-32449: Auftragsverlauf ist langsam oder wird mit Fehler 503 nicht geladen

Der Patch MDVA-32449 behebt das Problem in Adobe Commerce, bei dem der Auftragsverlauf langsam lädt oder nicht lädt und ein 503-Fehler angezeigt wird. Dies ist ein Problem, bei dem 13000+ Kunden einem B2B-Unternehmen zugewiesen werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 installiert ist. Bitte beachten Sie, dass dieses Problem in Adobe Commerce 2.4.1 behoben wurde.

## Betroffene Produkte und Versionen

Dies ist ein Problem, bei dem 13000+ Kunden einem B2B-Unternehmen zugewiesen werden.

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.0 - 2.3.5-p2, 2.4.0, 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Behebung des Problems, bei dem der Auftragsverlauf sehr langsam geladen wird oder überhaupt nicht geladen wird.

<u>Voraussetzungen</u>:

mehr als 13000 Kunden, die einem B2B-Unternehmen zugewiesen sind

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei der Storefront als Unternehmensadministrator an.
1. Rufen Sie die Seite mit dem Auftragsverlauf für den Vertrieb auf.

<u>Erwartete Ergebnisse</u>:

Die Verlaufsseite der Verkaufsaufträge wird normal geladen.

<u>Tatsächliche Ergebnisse</u>:

Die Seite wird sehr langsam geladen, oder die Seite wird möglicherweise nicht geladen, und es wird ein Timeout-Fehler angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie in der [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
