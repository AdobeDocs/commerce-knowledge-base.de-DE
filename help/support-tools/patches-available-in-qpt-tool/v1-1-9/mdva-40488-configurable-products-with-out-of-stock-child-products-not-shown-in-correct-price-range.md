---
title: "MDVA-40488: Konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten, die nicht in der richtigen Preisspanne angezeigt werden"
description: Der Patch MDVA-40488 behebt das Problem, dass konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten nicht in ihrer korrekten Preisspanne angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-40488. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: 0c4b9f5e-ae41-409e-b244-1d7cf948ed6f
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# MDVA-40488: Konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten werden nicht in der richtigen Preisspanne angezeigt

Der Patch MDVA-40488 behebt das Problem, dass konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten nicht in ihrer korrekten Preisspanne angezeigt werden. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 ist installiert. Die Patch-ID lautet MDVA-40488. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten werden nicht in der korrekten Preisspanne angezeigt.

<u>Voraussetzungen</u>:

Navigieren Sie zu Commerce Admin > **Stores** > **Konfiguration** > **Katalog** > **Bestand** > **Aktienoptionen** und **Nicht vorrätige Produkte anzeigen** Konfiguration auf *Ja*.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit zwei zugehörigen Produkten. Beispiel: einfache Produkte Rot und Braun.
1. Legen Sie das Inventar des einfachen Produkts Red fest und setzen Sie den Lagerstatus auf . *Auf Lager* und legen Sie dann den Status Produkt aktivieren auf *Nein*.
1. Legen Sie den Bestand des einfachen Produkts braun fest und setzen Sie dann den Status Produkt aktivieren auf *Ja*.
1. Stellen Sie sicher, dass der konfigurierbare Produktspeicherstatus lautet. *Auf Lager*.
1. Ändern Sie das Inventar des einfachen Produkts braun auf 0 und setzen Sie den Lagerstatus auf . *Nicht vorrätig*.
1. An dieser Stelle ist der konfigurierbare Produktstatus weiterhin *Auf Lager*.
1. Führen Sie eine Neuindizierung durch.
1. Überprüfen Sie die `min_price` und `max_price` für das konfigurierbare Produkt im `catalog_product_index_price` DB-Tabelle - die beiden Werte sind auf 0 festgelegt.
1. Wenn wir jedoch den konfigurierbaren Produktstatus auf *Nicht vorrätig* und reinindizieren, dann können wir sehen, dass ungleich null ist `min_price` und `max_price` -Werte des konfigurierbaren Produkts.

<u>Erwartete Ergebnisse</u>:

Wenn alle untergeordneten Produkte *Nicht vorrätig* und das konfigurierbare Produkt selbst *Nicht vorrätig*, wird der Preis unter Verwendung aller untergeordneten Produkte berechnet.

<u>Tatsächliche Ergebnisse</u>:

Die `min_price` und `max_price` -Werte für das konfigurierbare Produkt in der `catalog_product_index_price` Die DB-Tabelle wird auf 0 gesetzt, wenn der konfigurierbare Bestandsstatus *Auf Lager*, aber wenn es *Nicht vorrätig* werden sie zu Werten ungleich null.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
