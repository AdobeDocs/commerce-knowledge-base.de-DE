---
title: 'MDVA-13203 Patch: 503 Fehler Homepage Post full reindex'
description: 'Der Patch "MDVA-13203 Adobe Commerce"behebt das Problem, dass auf Ihrer Site eine Wartungsseite angezeigt wird und *CRITICAL: SQLSTATE\[23000\]: Fehler wegen Integritätseinschränkungen* im "system.log"auftreten. Die Patch-ID lautet MDVA-13203. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 installiert ist.'''
exl-id: 8e09010b-9aa4-4a79-b546-a24bb72e0e40
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-13203 Patch: 503 Fehler Homepage Post vollständige Neuindizierung

Der MDVA-13203 Adobe Commerce-Patch behebt das Problem, dass auf Ihrer Site eine Wartungsseite angezeigt wird und *CRITICAL: SQLSTATE\[23000\]: Fehler wegen Integritätseinschränkungen* in der `system.log` aufgetreten sind. Die Patch-ID lautet MDVA-13203. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 installiert ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce in der Cloud-Infrastruktur 2.2.4.

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0-2.4.1.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte:</u>

1. Rufen Sie die betroffene URL auf.
1. Sie sehen die Wartungsseite.
1. Vergewissern Sie sich, dass die Site nicht über SSH im Wartungsstatus ist:
   <pre> bin/magento maintenance:status
    Status: Wartungsmodus ist nicht aktiv
    Liste der ausgenommenen IP-Adressen: keine</pre>
1. Sehen Sie sich `system.log` an:

<pre>grep critical -i var/log/system.log |tail

[2018-09-04 17:05:18] report.CRITICAL: SQLSTATE[23000]: Integrity constraint verletzungen: 1062 Doppelter Eintrag '4613' für Schlüssel 'PRIMÄR', Abfrage lautete: INSERT INTO search_tmp_5b8eb4e 994da5_88027289` (`entity_id`,`score`) WERTE (?, ?),... (?, ?), (?, ?) [] []
[2018-09-04 17:05:21] report.CRITICAL: SQLSTATE[23000]: Integrity constraint verletzungen: 1062 Doppelter Eintrag '4613' für Schlüssel 'PRIMÄR', Abfrage lautete: INSERT INTO search_tmp_5b8ebb5 1579943_52333638` (`entity_id,`score`) WERTE (?, ?),...,(?, ?) [] []
[2018-09-04 17:05:47] report.CRITICAL: SQLSTATE[23000]: Integrity constraint verletzungen: 1062 Doppelter Eintrag '1350' für Schlüssel 'PRIMÄR', Abfrage lautete: INSERT INTO search_tmp_5b8ebb6b 7028f4_68065024` (`entity_id`,`score`) WERTE (?, ?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?) [] []
[2018-09-04 17:05:47] report.CRITICAL: SQLSTATE[23000]: Integrity constraint verletzungen: 1062 Doppelter Eintrag '1350' für Schlüssel 'PRIMÄR', Abfrage lautete: INSERT INTO search_tmp_5b8ebb6b 7885a9_23360993` (`entity_id`,`score`) WERTE (?, ?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?) [] []

date

Tue Sep 4 17:06:11 UTC 2018</pre>

<u>Erwartete Ergebnisse:</u> Sie sollten die Site sehen.

<u>Tatsächliche Ergebnisse:</u> Die Wartungsseite wird aufgrund von Problemen mit der Datenbankkonsistenz angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
