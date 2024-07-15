---
title: "MDVA-33281 Patch: Inventarinkonsistenzprobleme"
description: Der Patch MDVA-33281 behebt drei Inventarinkonsistenzprobleme. Klicken Sie auf die verknüpften Probleme im Abschnitt Problem , um die Schritte zum Reproduzieren dieser Fehler anzuzeigen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14 installiert ist.
exl-id: adba9728-6e42-467e-943d-cf8af0bec353
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# MDVA-33281 Patch: Probleme mit Bestandsinkonsistenz

Der Patch MDVA-33281 behebt drei Inventarinkonsistenzprobleme. Klicken Sie auf die verknüpften Probleme im Abschnitt Problem , um die Schritte zum Reproduzieren dieser Fehler anzuzeigen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14 installiert ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.4 - 2.3.5 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Patch behebt Bestandsinkonsistenzprobleme wie:

* **PHP Schwerwiegender Fehler** bei der Ausführung von `bin/magento inventory:reservation:list-inconsistencies` in der CLI aufgrund des falschen SKU-Parametertyps.
* **Duplizieren von Daten** in der Liste der Inkonsistenzen.
* **Neue Reservierung** wird vor der Bestellung erstellt (vorherige Realisierung basierend auf der Reservierung nach der Bestellung). Bei Fehlern bei der Bestellplatzierung wird eine zusätzliche Reservierung hinzugefügt, um einen Ausgleich zu erhalten.

>[!NOTE]
>
>Es gibt auch einen Patch MDVA-30112, der das Problem behebt, bei dem eine unerwartete große Anzahl von [Reservierungsinkonsistenzen](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) in unserer Entwicklerdokumentation in der `inventory_reservation` -Tabelle vorhanden ist. Informationen zur Lösung finden Sie unter [MDVA-30112 Magento Patch: Large number Reservierungsinkonsistenzen](/help/support-tools/patches-available-in-qpt-tool/v1-0-8/mdva-30112-magento-patch-large-number-reservation-inconsistencies.md) in unserer Support-Wissensdatenbank.

## Schwerwiegender PHP-Fehler

<u>Zu reproduzierende Schritte</u>:

PHP Schwerwiegender Fehler bei der Ausführung von `bin/magento inventory:reservation:list-inconsistencies`.

Um eine Liste von Reservierungsinkonsistenzen zu erhalten, melden Sie sich beim Produktionsserver an und führen Sie den folgenden Befehl in der CLI aus (-r switch - raw output):

<pre>bin/magento inventory:reservation:list-inkonsistences -r</pre>

<u>Erwartete Ergebnisse</u>:

Die Liste der Reservierungsinkonsistenzen wird erstellt. Diese werden im folgenden Format zurückgegeben

```plaintext
<ORDER_INCREMENT_ID>:<SKU>:<QUANTITY>:<STOCK-ID>
```

<u>Tatsächliche Ergebnisse</u>:

PHP Fatal Error wird ausgegeben.

## Daten duplizieren

Doppelte Daten befinden sich im `inventory_reservation table`.

<u>Zu reproduzierende Schritte</u>:

Führen Sie den folgenden Befehl aus, um Reservierungsinkonsistenzen zu beheben:

<pre>SELECT *, COUNT(*)
VON inventory_reserve
GRUPPE NACH Metadaten, SKU, Menge
HAVING COUNT(*) &gt; 1</pre>

<u>Erwartete Ergebnisse</u>:

Keine Duplikate.

<u>Tatsächliche Ergebnisse</u>:

Es gibt Duplikate.

## Neue Reservierung

<u>Zu reproduzierende Schritte</u>:

Neue Reservierung vor Bestellung erstellt:

1. Importieren Sie die Datenbank.
1. Führen Sie `bin/magento setup:upgrade` im Terminal aus.
1. Inkonsistenzen durch Ausführen von `bin/magento inventory:reservation:list-inconsistencies        -i -r` im Terminal auflisten.

<u>Erwartete Ergebnisse</u>:

Keine Schleife und viel schnellere Ergebnisse.

<u>Tatsächliche Ergebnisse</u>:

Die gleichen Ergebnisse werden in einer Endlosschleife angezeigt oder der Befehl schlägt je nach Systemeinstellungen mit `memory_limit` fehl.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie in der [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
