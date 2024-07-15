---
title: "MDVA-32313 Patch: Produkte, die der Wunschliste mit falscher Konfiguration hinzugefügt wurden"
description: Der Patch MDVA-32313 löst das Problem, dass konfigurierbare Produkte nicht korrekt zur Wunschliste hinzugefügt werden können, da ihnen falsche Konfigurationen zugewiesen werden, wenn sie zur Wunschliste hinzugefügt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.2 behoben wurde.
exl-id: e7ac5ef5-1389-4108-b2bc-73d43eb3e7ca
feature: Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# MDVA-32313 Patch: Produkte, die der Wunschliste mit falscher Konfiguration hinzugefügt wurden

Der Patch MDVA-32313 löst das Problem, dass konfigurierbare Produkte nicht korrekt zur Wunschliste hinzugefügt werden können, da ihnen falsche Konfigurationen zugewiesen werden, wenn sie zur Wunschliste hinzugefügt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.0

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.0 - 2.3.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen Kunden.
1. Melden Sie sich beim Kundenkonto an.
1. Navigieren Sie zur Seite **Produktauflistung** .
1. Wählen Sie ein konfigurierbares Produkt (Beispiel: *konfigurierbar\_1* ) und wählen Sie auf der Seite **Produktauflistung** die gewünschten Farb- und Größenoptionen aus (**Öffnen Sie die Produktseite nicht.**).
1. Klicken Sie auf das Wunschlistensymbol eines anderen konfigurierbaren Produkts (Beispiel: *konfigurierbar\_2*) auf derselben Seite, ohne Farb-/Größenoptionen auszuwählen.

<u>Erwartete Ergebnisse</u>:

Das Produkt *konfigurierbar\_2* wird wie erwartet ohne ausgewählte Optionen auf die Wunschliste gesetzt.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt *konfigurierbar\_2* wurde der Wunschliste mit der Konfiguration aus dem Produkt *konfigurierbar\_1* hinzugefügt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie in der [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
