---
title: "MDVA-31168 Patch: Produktexport-Datei wird nicht in Admin angezeigt"
description: Der Patch MDVA-31168 behebt das Problem, dass die CSV-Datei für den Produktexport nicht in der Liste der exportierbaren CSV-Dateien angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.2 behoben wurde.
exl-id: 780a926b-2aea-47c2-8f95-907cc779bfa4
feature: Admin Workspace, Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# MDVA-31168 Patch: Die Produktexport-Datei wird nicht in Admin angezeigt

Der Patch MDVA-31168 behebt das Problem, dass die CSV-Datei für den Produktexport nicht in der Liste der exportierbaren CSV-Dateien angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce lokal 2.3.5-p2.

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce in der Cloud-Infrastruktur und Adobe Commerce On-Premise 2.3.0 - 2.4.1.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Voraussetzungen</u>:

Installieren Sie Adobe Commerce mit Beispieldaten.

<u>Zu reproduzierende Schritte:</u>

1. Erstellen Sie ein herunterladbares Produkt und weisen Sie es der Kategorie **Bags** zu.
1. Starten Sie einen Export für alle Produkte.
1. Führen Sie folgenden Befehl aus der CLI aus:    ```php    bin/magento queue:consumers:start exportProcessor --single-thread --max-messages=10000    ```

<u>Erwartete Ergebnisse:</u>

Die CSV-Datei für den Produktexport mit allen Produkten wird wie erwartet in der Dateiliste in Admin angezeigt.

<u>Tatsächliche Ergebnisse:</u>

Die CSV-Datei für den Produktexport mit allen Produkten wird nicht in der Liste in Admin angezeigt, obwohl die Datei mit Kopfzeilen nur im Ordner &quot;`/var`&quot;auf dem Server generiert wird.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
