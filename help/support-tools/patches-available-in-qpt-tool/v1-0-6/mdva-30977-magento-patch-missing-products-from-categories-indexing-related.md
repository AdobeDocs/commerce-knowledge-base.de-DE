---
title: "MDVA-30977: fehlende Produkte aus Kategorien, Indizierungsbezogene Produkte"
description: Der Patch MDVA-30977 behebt die Probleme mit Produkten, die bei Neuindizierungen oder Massenaktionen mit einer großen Anzahl von Produkten auf Storefront-Kategorieseiten angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 installiert ist. Die Probleme sollen in Adobe Commerce 2.4.2 behoben werden.
exl-id: 66ec4f53-c01d-4f87-a175-84f44a26f5d3
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# MDVA-30977: fehlende Produkte aus Kategorien, Indizierungsbezogene

Der Patch MDVA-30977 behebt die Probleme mit Produkten, die bei Neuindizierungen oder Massenaktionen mit einer großen Anzahl von Produkten auf Storefront-Kategorieseiten angezeigt werden. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 installiert ist. Die Probleme sollen in Adobe Commerce 2.4.2 behoben werden.

## Betroffene Produkte und Versionen

Der Patch wurde für Adobe Commerce in der Cloud-Infrastruktur 2.3.4 erstellt. Sie ist auch mit Adobe Commerce vor Ort 2.3.4 vereinbar.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Probleme

### Problem 1

Die Anzahl der Produkte, die auf der Kategorieseite in der Storefront angezeigt werden, unterscheidet sich nach jeder Seitenneuladung während der Massenaktualisierung des Produkts.

<u>Zu reproduzierende Schritte:</u>

1. Erstellen Sie mindestens 30000 Produkte in zwei Kategorien - mindestens 15000 Produkte in jeder Kategorie.
1. Navigieren Sie zu **Katalog** > **Produkte** in der Commerce-Admin.
1. Wählen Sie alle Produkte aus dem Raster aus und führen Sie eine Massenattributaktualisierung durch. Legen Sie beispielsweise **Neu** = *Ja* -Attribut.
1. Führen Sie den Magento-Cron-Auftrag mit dem `bin/magento cron:run` -Befehl.
1. Aktualisieren Sie Kategorieseiten auf der Storefront, während Adobe Commerce 30.000 Produktaktualisierungen durchführt.

<u>Erwartetes Ergebnis:</u>

Die Anzahl der Produkte in Kategorien beträgt bei jeder Kategorieseitenaktualisierung immer 15000.

<u>Ergebnis:</u>

Die Anzahl der Produkte in Kategorien ist bei jeder Kategorieseitenaktualisierung unterschiedlich.

### Problem 2

Wenn die vollständige Neuindizierung des Bestands ausgeführt wird, werden Kategorieseiten leer und die *Wir können keine der Auswahl entsprechenden Produkte finden* angezeigt.

<u>Zu reproduzierende Schritte:</u>

1. Konfigurieren Sie Adobe Commerce mit Elasticsearch.
1. Hinzufügen einer neuen Website.
1. Erstellen Sie eine neue Quelle und weisen Sie sie der neuen Website mithilfe von &quot;Lager verwalten&quot;zu.
1. Erstellen Sie 30000 konfigurierbare Produkte.
1. Weisen Sie alle Produkte der neuen Website zu und fügen Sie der neuen Inventarquelle auch Inventar hinzu.
1. Führen Sie eine vollständige Neuindizierung aus.
1. Führen Sie die Neuindizierung des Bestands durch, indem Sie `bin/magento indexer:reindex inventory`
1. Durchsuchen Sie eine Kategorie mit einer großen Anzahl von Produkten.

<u>Erwartetes Ergebnis:</u>

Kategorieseiten zeigen Produkte wie gewohnt während der Neuindizierung an.

<u>Ergebnis:</u>

Kategorieseiten werden während der Neuindizierung leer.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) Abschnitt.
