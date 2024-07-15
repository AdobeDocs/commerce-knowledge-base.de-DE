---
title: "MDVA-11189: cataloginventory_stock rows Gelöscht Post CSV Import"
description: Der Adobe Commerce-Patch MDVA-11189 behebt das Problem, wenn nach dem Import einer CSV-Datei zur Aktualisierung des Produktbestands Zeilen aus der Tabelle "cataloginventory_stock"gelöscht werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 installiert ist. Die Patch-ID lautet MDVA-1189. Beachten Sie, dass das Problem in Adobe Commerce 2.3.5 behoben wurde.
exl-id: 84e1979c-826c-4c01-b0c7-8054bb4b23f0
feature: Catalog Management, Data Import/Export, Inventory, Orders
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# MDVA-11189: cataloginventory_stock Zeilen gelöscht Post CSV Import

Der Adobe Commerce-Patch MDVA-11189 behebt das Problem, wenn nach dem Import einer CSV-Datei zur Aktualisierung des Produktbestands Zeilen aus der `cataloginventory_stock`-Tabelle gelöscht werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 installiert ist. Die Patch-ID lautet MDVA-1189. Beachten Sie, dass das Problem in Adobe Commerce 2.3.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce in der Cloud-Infrastruktur 2.2.3

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0-2.3.4-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Behebt das Problem, wenn nach dem Import von `.csv` zur Aktualisierung des Produktbestands Zeilen aus der `cataloginventory_stock` -Tabelle gelöscht werden.

<u>Zu reproduzierende Schritte:</u>

1. Führen Sie in der Datenbank den folgenden MySQL-Befehl aus: `select count(*) from cataloginventory_stock_status;`
1. Notieren Sie die Anzahl der Zeilen.
1. Legen Sie die Registerkarte &quot;crontab&quot;wie folgt fest: `* * * * * /usr/bin/php <path to installation>/bin/magento cron:run  | grep -v "Ran jobs by schedule" >> <path to installation>/var/log/cron.log 2>&1`
1. Wechseln Sie zum Admin-Bedienfeld unter **System** > **Tools** > **Indexverwaltung**.
1. Setzen Sie die Indexer auf *Nach Zeitplan aktualisieren* .
1. Wechseln Sie zu **System** > *Datenübertragung* > **Export**.
1. Setzen Sie **Entitätstyp** auf *Produkte* > **Weiter**.
1. Öffnen Sie die gespeicherte Datei &quot;`.csv`&quot;> Entfernen Sie alle Spalten außer SKU und QTY.
1. Aktualisieren Sie die Menge für alle Produkte auf 150.
1. Speichern Sie die Datei &quot;`.csv`&quot;.
1. Wechseln Sie zu **System** > *Datenübertragung* > **Import** .
1. Legen Sie die folgenden Werte fest:
   1. Entitätstyp: *Products*
   1. Importverhalten: *Hinzufügen/Aktualisieren*
   1. Behalten Sie alle anderen Werte standardmäßig bei.
   1. Wählen Sie Datei aus, um die Tabelle mit den Katalogprodukten auszuwählen.
1. Klicken Sie auf **Daten überprüfen** > **Importieren**. Es dauert 5 bis 10 Minuten.
1. Führen Sie in der Datenbank den folgenden MySQL-Befehl aus:
   `select count(*) from cataloginventory_stock_status;`

<u>Tatsächliches Ergebnis:</u>

Die Anzahl der Zeilen in `cataloginventory_stock` wird nach dem CSV-Import verringert, um den Bestand zu aktualisieren.

<u>Erwartetes Ergebnis:</u>

Die Anzahl der Zeilen in `cataloginventory_stock` sollte nach dem CSV-Import gleich bleiben, um den Bestand zu aktualisieren.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
