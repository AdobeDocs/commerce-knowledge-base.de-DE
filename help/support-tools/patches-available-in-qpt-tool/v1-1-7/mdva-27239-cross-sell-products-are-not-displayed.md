---
title: "MDVA-27239: Cross-Sell-Produkte werden nicht angezeigt"
description: Der Patch MDVA-27239 behebt das Problem, dass Crosssell-Produkte nicht angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.3.6 behoben wurde.
exl-id: a0392a07-645d-4811-8547-2c67e20b6313
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-27239: Querverkaufsprodukte werden nicht angezeigt

Der Patch MDVA-27239 behebt das Problem, dass Crosssell-Produkte nicht angezeigt werden. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 ist installiert. Beachten Sie, dass das Problem in Adobe Commerce 2.3.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4, 2.4.0

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.3.5-p2, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Cross-Sell-Produkte werden nicht im Querverkaufsblock auf der Warenkorbseite angezeigt.

<u>Voraussetzungen</u>:

1. Deaktivieren Sie das Magento_TargetRule-Modul oder entfernen Sie es aus dem Layout-Block Magento\TargetRule\Block\Checkout\Cart\Crosssell.
1. Produkt erstellen 1.
1. Erstellen Sie ein Planupdate für Produkt 1, sodass die neu erstellten Produkte eine andere Zeile_ID als entity_id aufweisen.
1. Erstellen Sie Produkt 2, Produkt 3 und Produkt 4.
1. Legen Sie Produkt 3 als Crosssell für Produkt 4 fest.
1. Legen Sie Produkt 4 als Crosssell für Produkt 2 fest.

<u>Zu reproduzierende Schritte</u>:

1. Fügen Sie Produkt 4 und Produkt 2 zum Warenkorb hinzu.
1. Überprüfen Sie die Warenkorbseite.

<u>Erwartete Ergebnisse</u>:

Produkt 3 wird in Querverkaufsblöcken angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Der Querverkaufsblock ist leer.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
