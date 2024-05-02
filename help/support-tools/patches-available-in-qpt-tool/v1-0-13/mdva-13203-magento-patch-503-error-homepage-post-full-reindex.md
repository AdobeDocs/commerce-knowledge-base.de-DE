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

Der MDVA-13203 Adobe Commerce-Patch behebt das Problem, dass Ihre Site eine Wartungsseite anzeigt und es *KRITISCH: SQLSTATE\[23000\]: Verletzung der Integritätsbeschränkung* Fehler in `system.log`. Die Patch-ID lautet MDVA-13203. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 installiert ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce auf Cloud-Infrastruktur 2.2.4.

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0-2.4.1.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte:</u>

1. Rufen Sie die betroffene URL auf.
1. Sie sehen die Wartungsseite.
1. Vergewissern Sie sich, dass die Site nicht über SSH im Wartungsstatus ist:
   <pre> bin/magento-Wartung:Status: Wartungsmodus ist nicht aktiv Liste der ausgenommenen IP-Adressen: keine</pre>
1. Sehen Sie sich an `system.log`:

<pre>grep critical -i var/log/system.log |tail [2018-09-04 17:05:18] report.CRITICAL: SQLSTATE[23000]: Integrity constraint verletzungen: 1062 Doppelter Eintrag '4613' für Schlüssel 'PRIMÄR', Abfrage war: INSERT IN `search_tmp_5b8ebb4e994da5_8802728 9` (`entity_id,`score`) WERTE (?, ?),... (?, ?), (?, ?), (?, ?) [] [] [2018-09-04 17:05:21] report.CRITICAL: SQLSTATE[23000]: Integrity constraint verletzungen: 1062 Doppelter Eintrag '4613' für Schlüssel 'PRIMÄR', Abfrage war: INSERT IN `search_tmp_5b8ebb5157943_5233 3638` (`entity_id,`score`) WERTE (?, ?),...,(?, ?) [] [] [2018-09-04 17:05:47] report.CRITICAL: SQLSTATE[23000]: Integrity constraint verletzungen: 1062 Doppelter Eintrag '1350' für Schlüssel 'PRIMÄR', Abfrage war: INSERT IN `search_tmp_5b8ebb6b7028f4_680650 24` (`entity_id`,`score`) WERTE (?, ?), (?, ?), (?, ?, ?), (?, ?, ?), (?, ?, ?), (?, ?, ?), (?, ?), (?, ?, ?), (?, ?, ?), (?, ?), (?, ?), (?,) [] [] [2018-09-04 17:05:47] report.CRITICAL: SQLSTATE[23000]: Integrity constraint verletzungen: 1062 Doppelter Eintrag '1350' für Schlüssel 'PRIMÄR', Abfrage war: INSERT IN `search_tmp_5b8ebb6b7885a9_23609 93` (`entity_id`,`score`) WERTE (?, ?), (?, ?), (?, ?, ?), (?, ?, ?), (?, ?, ?), (?, ?, ?), (?, ?), (?, ?, ?), (?, ?, ?), (?, ?), (?, ?), (?,) [] [] Datum Tue Sep 4 17:06:11 UTC 2018</pre>

<u>Erwartete Ergebnisse:</u> Sie sollten die Site sehen.

<u>Ergebnisse:</u> Die Wartungsseite wird aufgrund von Problemen mit der Datenbankkonsistenz angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
