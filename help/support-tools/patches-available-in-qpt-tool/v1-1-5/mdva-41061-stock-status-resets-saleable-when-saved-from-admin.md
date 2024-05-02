---
title: "MDVA-41061: Der Lagerstatus wird beim Speichern des Produkts unter Admin auf verkäuflich zurückgesetzt."
description: Der Patch MDVA-41061 behebt das Problem, dass der Lagerstatus beim Speichern des Produkts vom Administrator auf verkäuflich zurückgesetzt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41061. Die neueste Patch-Version ist in QPT 1.1.15 mit der Patch-ID MDVA-41061-V3 verfügbar. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.
exl-id: fd71d3e5-685f-4987-b7e7-bfd86810d865
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-41061: Der Lagerstatus wird auf verkäuflich zurückgesetzt, wenn das Produkt über Admin gespeichert wird

Der Patch MDVA-41061 behebt das Problem, dass der Lagerstatus beim Speichern des Produkts vom Administrator auf verkäuflich zurückgesetzt wird. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5 ist installiert. Die Patch-ID lautet MDVA-41061. Die neueste Patch-Version ist in QPT 1.1.15 mit der Patch-ID MDVA-41061-V3 verfügbar. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.2-p2, 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Lagerstatus wird beim Speichern des Produkts vom Administrator auf verkäuflich zurückgesetzt.

<u>Voraussetzungen</u>:

Die Inventarmodule sind installiert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein einfaches Produkt mit Menge = 1.
1. Platzieren Sie eine Bestellung mithilfe des in Schritt 1 erstellten Produkts.
1. cron ausführen - Stellen Sie sicher, dass `inventory.reservations.updateSalabilityStatus` -Warteschlange ausgeführt und der Status des Produktbestands wurde in `cataloginventory_stock_status` Tabelle.
1. Überprüfen Sie das Produkt auf der Vorderseite. Sie sollte als **Nicht vorrätig**.
1. Speichern Sie das Produkt in der Admin-Konsole ohne Änderungen.

<u>Erwartete Ergebnisse</u>:

* Der Lagerstatus sollte nicht aktualisiert werden.
* Das Produkt sollte **Nicht vorrätig** an der Front.

<u>Tatsächliche Ergebnisse</u>:

* Einfaches Produkt wird als **Auf Lager** an der Front.
* Benutzer erhalten *Die angeforderte Menge ist nicht verfügbar* Meldung beim Versuch, sie dem Warenkorb hinzuzufügen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
