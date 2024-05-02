---
title: '"MDVA-28993: Teilsuche im Elasticsearch, "Mindest sollte übereinstimmen"und Fehlerbehebung für das Problem "Suchvorgänge mit Bindestrich"'
description: Der Patch MDVA-28993 implementiert die Funktionalität "Minimum should match"(Mindestanzahl sollte übereinstimmen) und die partielle Suche für die Elasticsearch-Engine und löst Probleme mit Bindestrichen in Suchabfragen. Der Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 installiert ist.
exl-id: 2af0f950-284b-42f2-9660-8aafce4b04d7
feature: Search, Services
role: Admin
source-git-commit: 6f4d6382cbdb7bedddcc3f264fbf6ef997729323
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-28993: Problem mit partieller Suche im Elasticsearch, &quot;Mindest sollte übereinstimmen&quot;und Fehlerbehebung für &quot;Suchen mit Bindestrich&quot;

Der Patch MDVA-28993 implementiert die Funktionalität &quot;Minimum should match&quot;(Mindestanzahl sollte übereinstimmen) und die partielle Suche für die Elasticsearch-Engine und löst Probleme mit Bindestrichen in Suchabfragen. Der Patch ist verfügbar, wenn die [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 installiert ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce in Cloud-Infrastruktur 2.3.4

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce On-Premise/Adobe Commerce für Cloud-Infrastruktur 2.3.4-2.3.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.


## Problem

Wenn Sie Elasticsearch 6 zum Suchen der SKU verwenden, die einen Bindestrich (-) enthält, gibt die Suche zu viele Ergebnisse zurück.

<u>Zu reproduzierende Schritte:</u>

1. Gehen Sie zur Storefront.

1. Geben Sie in der Suchleiste eine Zeichenfolge ein, die einen Bindestrich enthält, z. B. &quot;WS-M-Blue&quot;.

<u>Erwartetes Ergebnis:</u>

Gibt nur WS-M-Blue zurück.

<u>Ergebnis:</u>

Gibt alle SKUs zurück, die mit &quot;WS&quot;beginnen.

## Patch-Details

Der Patch MDVA-28993 enthält die folgenden Fehlerbehebungen und Verbesserungen:

* implementiert die neue Funktion &quot;Mindest sollte übereinstimmen&quot;und die Teilsuche nach der Elasticsearch-Engine. Weitere Informationen zur Konfiguration finden Sie unter [Konfigurieren der Katalogsuche](https://docs.magento.com/user-guide/catalog/search-configuration.html#step-4-configure-minimum-terms-to-match) in unserem Benutzerhandbuch.
* Teilsuche nach Elasticsearch
* behebt das oben beschriebene Problem &quot;Suchvorgänge mit Bindestrich&quot;.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) Abschnitt.
