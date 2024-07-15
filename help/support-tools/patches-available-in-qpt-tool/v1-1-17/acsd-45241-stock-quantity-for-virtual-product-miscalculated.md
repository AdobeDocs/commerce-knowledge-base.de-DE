---
title: "ACSD-45241: falsch berechnete Lagerbestände des Virtual-Product-Produkts"
description: Der Patch ACSD-45241 behebt das Problem, bei dem die Lagermenge des virtuellen Produkts nach der Erstellung eines Kreditmemos falsch berechnet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 installiert ist. Die Patch-ID lautet ACSD-45241. Beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.
exl-id: 4be97da9-d399-419a-816e-cf65f15cc3be
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# ACSD-45241: falsch berechnete Lagerbestände des Virtual-Produkts

Der Patch ACSD-45241 behebt das Problem, bei dem die Lagermenge des virtuellen Produkts nach der Erstellung eines Kreditmemos falsch berechnet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 installiert ist. Die Patch-ID lautet ACSD-45241. Beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Lagermenge für ein virtuelles Produkt wird nach der Erstellung eines Credit Memos falsch berechnet.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie in Commerce Admin ein konfigurierbares Produkt mit einem virtuellen Produkt als untergeordnetes Produkt.
1. Stellen Sie sicher, dass beide in Schritt 1 erstellten Produkte auf Lager sind.
1. Markieren Sie die Menge für das in Schritt 1 erstellte virtuelle Produkt als 100 und behalten Sie auch die Verkaufsmenge 100 bei.
1. Fügen Sie das Produkt zum Warenkorb hinzu.
1. Platzieren Sie eine Bestellung mit dem in Schritt 1 erstellten virtuellen Produkt.
1. Behalten Sie den Bestellstatus &quot;Ausstehend&quot; bei. Die Zahlung muss nicht verarbeitet werden.
1. `order_created` Datensatz erstellt in `inventory_reservation`. Die virtuelle Produktmenge zeigt 100 mit einer Verkaufsmenge von 99.
1. Öffnen Sie die Bestellung und gehen Sie zu **Rechnung** > **Rechnung senden**.
1. `invoice_created` Datensatz erstellt in `inventory_reservation`. Die virtuelle Produktmenge ist jetzt 99 und die Verkaufsmenge beträgt ebenfalls 99.
1. Erstellen Sie ein Kreditmemo, ohne **Zurück auf Lager** auszuwählen.

<u>Erwartete Ergebnisse</u>:

In `inventory_reservation` wird kein neuer Datensatz erstellt und die Lagermenge für das virtuelle Produkt bleibt unverändert.

<u>Tatsächliche Ergebnisse</u>:

Ein `creditmemo_created` -Datensatz wird in `inventory_reservation` erstellt und die virtuelle Produktvorratenmenge wird auf 98 mit einer Verkaufsmenge von 99 angepasst.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
