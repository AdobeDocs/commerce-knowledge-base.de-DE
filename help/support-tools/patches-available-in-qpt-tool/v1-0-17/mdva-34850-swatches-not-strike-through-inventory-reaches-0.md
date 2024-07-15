---
title: '"MDVA-34850: Muster, die nicht durchgestrichen werden, erreichen "0"'
description: Der Patch MDVA-34850 behebt das Problem, dass die Farbfelder nicht durchbrochen werden, wenn der Bestand "0"erreicht, und nicht im Link Produktdetailseite (PDP) zu anderen In-Stock-Farbfeldern sichtbar sind. "Nicht vorrätige Produkte anzeigen"ist in der Admin-Konfiguration ebenfalls auf **Ja* gesetzt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: 90f5cef4-137a-426d-a447-2d1aca23e6c1
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# MDVA-34850: nicht durchgestrichene Farbmuster erreichen &quot;0&quot;

Der Patch MDVA-34850 behebt das Problem, dass die Farbfelder nicht durchbrochen werden, wenn der Bestand &quot;0&quot;erreicht, und nicht im Link Produktdetailseite (PDP) zu anderen In-Stock-Farbfeldern sichtbar sind. **Nicht vorrätige Produkte anzeigen** ist in der Admin-Konfiguration ebenfalls auf *Ja* eingestellt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce vor Ort und Adobe Commerce über Cloud-Infrastruktur 2.3.1 - 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nicht vorrätige Produktoptionen werden nicht auf der Produktdetailseite angezeigt, wenn der standardmäßige Lagerbestand nicht verwendet wird und die Konfiguration **Nicht vorrätige Produkte anzeigen** aktiviert ist.

<u>Voraussetzungen</u>:

* Installieren Sie Multi-Source Inventory (MSI).
* Aktivieren Sie &quot;Nicht vorrätige Produkte anzeigen&quot;in den Optionen für den Lagerbestand [.](https://docs.magento.com/user-guide/configuration/catalog/inventory.html)

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen neuen Lagerbestand \[Neuer Stock\], der alle Websites mit der oben genannten Quelle verknüpft. Jetzt sollte der Standardbestand nicht mehr verwendet werden.
1. Erstellen Sie ein [konfigurierbares Produkt](https://docs.magento.com/user-guide/catalog/product-create-configurable.html), das drei Größenoptionen \[S,M,L\] hinzufügt.
1. Öffnen Sie jede Option und fügen Sie Mengen hinzu, indem Sie nur die benutzerdefinierte Quelle &quot;\[new\_source\]&quot;zuweisen. Setzen Sie außerdem \[Source-Status\] auf \[Auf Lager\].
1. Neuindizieren und Überprüfen des konfigurierbaren Produkts vom Frontend. Alle drei Optionen sollten sichtbar sein.
1. Öffnen Sie ein einfaches Produkt, das \[size:S\] vom Backend zugewiesen wurde, und setzen Sie \[Source-Status\] auf \[Nicht auf Lager\]. Aktualisieren Sie auch die Menge auf 0. Neuindizieren und Überprüfen des konfigurierbaren Produkts vom Frontend.

<u>Erwartete Ergebnisse</u>:

Da die Option &quot;Nicht vorrätige Produkte anzeigen&quot;aktiviert ist, sollten alle drei Optionen angezeigt werden. Die Option &quot;Nicht auf Lager&quot;\[S\] sollte deaktiviert und übersprungen werden. Es sollte 2 x 1 Optionsprodukt mit Preis = 12x2 in Bestelldetails am Frontend und Backend anzeigen.

<u>Tatsächliche Ergebnisse</u>:

Die Option &quot;Nicht auf Lager&quot;ist ausgeblendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) verfügbare Patches.
