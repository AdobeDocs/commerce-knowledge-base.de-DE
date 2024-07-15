---
title: "MDVA-22383: langsam indizierende Zielregelindexer"
description: Der Patch MDVA-22383 behebt das Problem, dass die Neuindizierung der Produkt-/Target-Regel und der Target-Regel-/Produkt-Indexer zu lange dauert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 installiert ist. Die Patch-ID lautet MDVA-22383. Beachten Sie, dass das Problem in Adobe Commerce 2.3.5 behoben wurde.
exl-id: fbf28983-5883-4769-90bd-1c97c2b2e2b8
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-22383: Index der Zielregel wird langsam indiziert

Der Patch MDVA-22383 behebt das Problem, dass die Neuindizierung der Produkt-/Target-Regel und der Target-Regel-/Produkt-Indexer zu lange dauert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 installiert ist. Die Patch-ID lautet MDVA-22383. Beachten Sie, dass das Problem in Adobe Commerce 2.3.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce in der Cloud-Infrastruktur 2.3.2

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce für Cloud-Infrastruktur und Adobe Commerce On-Premise 2.3.0-2.3.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Neuindizierung der Produkt-/Target-Regel und der Target-Regel-/Produkt-Indizes dauert zu lange.

<u>Voraussetzungen:</u> Das Problem tritt auf, wenn eine große Anzahl von Produkten vorhanden ist.

<u>Zu reproduzierende Schritte:</u>

1. Erstellen Sie eine Zielregel mit Produkten, die den Bedingungen entsprechen. Die Bedingungen sollten mehr Produkt zur Sammlung hinzufügen und Attribute aufweisen (nicht Kategorien oder Attributsätze).
1. Führen Sie den folgenden Befehl aus:

   ```bash
       bin/magento indexer:reindex targetrule_product_rule
   ```

<u>Tatsächliches Ergebnis:</u>

Die Neuindizierung ist blockiert; die Produktspeicherung bleibt hängen.

<u>Erwartetes Ergebnis:</u>

Die Neuindizierung wurde erfolgreich abgeschlossen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) verfügbare Patches.
