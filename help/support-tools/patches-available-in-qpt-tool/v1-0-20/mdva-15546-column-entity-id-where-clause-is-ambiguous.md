---
title: "MDVA-15546: Column 'entity_id' where clause is ambiuous"
description: "Der Patch MDVA-15546 löst Leistungsprobleme, die möglicherweise mit einigen Amazon-Erweiterungen in Zusammenhang stehen. Dieses Problem wird durch den folgenden Fehler in den Ausnahmeprotokollen angezeigt: *wobei*   *Spalte 'entity\\_id', in der die Klausel mehrdeutig ist, lautet die Abfrage: SELECT \\`main\_table\\`.\\*, \\`extension\\_attribute\\_amazon\\_order\\_reference\\_id* \\`. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 installiert ist. Die Patch-ID lautet MDVA-15546."
exl-id: d58c1728-eb7a-49e8-a329-3197f2339b9c
feature: B2B, Commerce Intelligence
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-15546: Spalte &#39;entity_id&#39;, wobei die Klausel mehrdeutig ist

Der Patch MDVA-15546 löst Leistungsprobleme, die mit einigen Amazon-Erweiterungen zusammenhängen können. Dieses Problem wird durch den folgenden Fehler in den Ausnahmeprotokollen angezeigt: *wobei*   *Spalte &#39;entity\_id&#39;, in der die Klausel mehrdeutig ist, lautet die Abfrage: SELECT \`main\_table\`.\*, \`extension\_attribute\_amazon\_order\_reference\_id* \`. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 installiert ist. Die Patch-ID lautet MDVA-15546.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.2.5

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.0 - 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Leistungsprobleme, die sich auf einige Amazon-Erweiterungen beziehen können.

<u>Voraussetzungen</u>:

Bereinigen Sie Adobe Commerce mit B2B und Amazon\_Payment.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zur Storefront-Seite.
1. Produkt zum Warenkorb hinzufügen.
1. Warten oder Trigger des Cron-Auftrags `flush_preview_quotas`.

<u>Tatsächliches Ergebnis</u>:

Wenn Sie `var/log/exception/log` aktivieren, wird der folgende Fehler angezeigt:

*`report.ERROR: Cron Jobflush_preview_quotashas an error: SQLSTATE[23000]: Integrity constraint violation: 1052 Column 'entity_id' in where clause is ambiguous, query was: SELECT `main_table`.*, `extension_attribute_amazon_order_reference_id`.`amazon_order_reference_id` AS `extension_attribute_amazon_order_reference_af_reference_id_amazon_order_reference_id`, `extension_attribute_amazon_order_reference_id`.`Anführungszeichen_id` AS `extension_attribute_order_reference_id _attribute_amazon_order_reference_id`.` sandbox_simulation_reference` AS `extension_attribute_amazon_order_reference_id_sandbox_simulation_reference`, `extension_attribute_amazon_order_reference_id`.`bestätigte` AS `extension_attribute_amazon_order_reference_id_bestätigte` FROM `main_quoting` LEFT JOIN `amazon_quote` AS `extension_attribute_amazon_order_reference_id` ON main_table.entity_id = extension_attribute_amazon_order_reference_id.quote_id WHERE ...`*`, `` AS `

<u>Erwartetes Ergebnis</u>:

Cron Job wird ohne Fehler abgeschlossen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
