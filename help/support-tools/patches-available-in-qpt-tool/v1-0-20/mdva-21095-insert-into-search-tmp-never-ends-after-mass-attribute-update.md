---
title: '"MDVA-21095: EINFÜGEN IN "search_tmp..."endet nie nach der Aktualisierung des Massenattributs."'
description: Der Patch MDVA-21095 behebt das Problem, dass die Abfrage "INSERT INTO" "search\_tmp.." nach einem gebündelten Attribut-Update nie endet. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 installiert ist. Die Patch-ID lautet MDVA-21095. Bitte beachten Sie, dass es derzeit keinen Plan gibt, dieses Problem in zukünftigen Versionen zu beheben.
exl-id: fd599473-b49a-4f9c-a13f-612d05e43f09
feature: Attributes, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# MDVA-21095: EINFÜGEN IN &quot;search_tmp...&quot;endet nie nach der Aktualisierung des Massenattributs.

Der Patch MDVA-21095 behebt das Problem, dass die Abfrage `INSERT INTO` &quot;search\_tmp...&quot;nach einem gebündelten Attributupdate nie endet. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 installiert ist. Die Patch-ID lautet MDVA-21095. Bitte beachten Sie, dass es derzeit keinen Plan gibt, dieses Problem in zukünftigen Versionen zu beheben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.3.2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.3.4-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

`INSERT INTO` &quot;search\_tmp..&quot; endet nie nach einer Massenaktualisierung von Attributen.

<u>Schritt zum Reproduzieren</u>:

Führen Sie eine Aktualisierung der Massenattributwerte mit etwa 30.000 Elementen durch.

<u>Erwartete Ergebnisse</u>:

Der Neuindizierungsprozess wird wie erwartet normal abgeschlossen.

<u>Tatsächliche Ergebnisse</u>:

Der Neuindizierungsprozess ist abgeschlossen, aber viele Abfragen `INSERT INTO` &quot;search\_tmp...&quot;beginnen, bis der Server den `pm.max_children` -Parameterwert erreicht und PHP-fpm stirbt. Diese werden auch nach dem Neustart von MySQL und dem Abbruch von Prozessen ständig wiederholt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
