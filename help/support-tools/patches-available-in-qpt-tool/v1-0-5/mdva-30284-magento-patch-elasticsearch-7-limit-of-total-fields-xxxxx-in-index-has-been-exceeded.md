---
title: "MDVA-30284 Patch: Elasticsearch 7 - Die Beschränkung der Indexanzahl [XXXXX] wurde überschritten"
description: Der MDVA-30284-Patch behebt das Problem, bei dem Sie eine Fehlermeldung erhalten, dass bei Verwendung von Elasticsearch 7 die "Beschränkung der Gesamtfelder \[XXXXXXX\] im Index überschritten wurde". Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.5 installiert ist. Die Patch-ID lautet MDVA-30284.
exl-id: cf840558-891a-4a7e-8900-b8434f703be0
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Patch: Elasticsearch 7 - Begrenzung der Gesamtfelder [XXXXXXX] im Index überschritten wurde

Der MDVA-30284-Patch behebt das Problem, bei dem Sie eine Fehlermeldung erhalten, dass bei Verwendung von Elasticsearch 7 die &quot;Beschränkung der Gesamtfelder \[XXXXXXX\] im Index überschritten wurde&quot;. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.5 installiert ist. Die Patch-ID lautet MDVA-30284.

## Betroffene Produkte und Versionen

* Der Patch wurde für Adobe Commerce in der Cloud-Infrastruktur 2.3.5-p2 entwickelt.
* Elasticsearch 7 ist mit Adobe Commerce 2.3.5 und 2.4.x kompatibel

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Begrenzung der Elasticsearch-Felder ist falsch, was bei der Ausführung des Indexers \[catalogsearch\_fulltext\] zu folgendem Fehler führt:

*Begrenzung der Gesamtfelder [xxx] in Index [xxxxxx] wurde überschritten*

Dieses Problem tritt auf, wenn Sie über eine große Anzahl von Produktattributen verfügen. Das Problem wird durch die Art und Weise ausgelöst, wie Elasticsearch die Feldanzahl berechnet. Manchmal werden diese Felder bei Attributen, denen Felder zugewiesen sind, als separate Indexer indiziert. Dies führt dazu, dass die Begrenzung die Warnung überschritten hat.

<u>Zu reproduzierende Schritte:</u>

<u>Voraussetzungen</u>

* Installierte module-elasticsearch 100.3.5.
* Elasticsearch 7 installiert.
* Richten Sie Elasticsearch als Such-Backend ein.

1. Erstellen Sie mehr als 1000 Attribute für Produkte.
1. Erstellen Sie Produkte für jede Familie.
1. Führen Sie den Indexer aus.

<u>Erwartetes Ergebnis:</u>

Alle Elasticsearch sind im Produktindex verfügbar.

<u>Ergebnis:</u>

1. Elasticsearch error:

   ```
    {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"}],"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"},"status":400}
   ```

1. Neues Produkt wurde nicht indiziert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
