---
title: "MDVA-41139: Konfigurierbares Produkt wird nach dem Produktimport nicht mehr vorrätig"
description: Der Patch MDVA-41139 behebt das Problem, dass das konfigurierbare Produkt nach dem Produktimport außer Lager kommt, wenn die Menge des einfachen Produkts = 0 für eine seiner Quellen beträgt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-41139. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: e90ab578-50b9-4bc4-baf9-de4182e700ae
feature: Data Import/Export, Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-41139: Konfigurierbares Produkt wird nach dem Produktimport nicht mehr vorrätig

Der Patch MDVA-41139 behebt das Problem, dass das konfigurierbare Produkt nach dem Produktimport außer Lager kommt, wenn die Menge des einfachen Produkts = 0 für eine seiner Quellen beträgt. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 ist installiert. Die Patch-ID lautet MDVA-41139. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das konfigurierbare Produkt wird nach dem Produktimport nicht mehr vorrätig, wenn die Menge des einfachen Produkts = 0 für eine seiner Quellen beträgt.

<u>Voraussetzungen</u>:

Inventarmodule werden installiert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue Quelle und ein neues Lager.
1. Erstellen Sie ein konfigurierbares Produkt mit untergeordneten Produkten, die der Standardquelle und der neuen Quelle zugewiesen sind.
1. Legen Sie für jedes untergeordnete Produkt den Wert Standard Stock = 0 und für das andere Lager > 0 fest.
1. Das konfigurierbare Produkt ist auf Lager.
1. Exportieren Sie dieses Produkt und importieren Sie es erneut.

<u>Erwartete Ergebnisse</u>:

Das konfigurierbare Produkt ist auf Lager, da die zweite Quelle eine Menge > 0 aufweist.

<u>Tatsächliche Ergebnisse</u>:

Das konfigurierbare Produkt ist nicht vorrätig.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
