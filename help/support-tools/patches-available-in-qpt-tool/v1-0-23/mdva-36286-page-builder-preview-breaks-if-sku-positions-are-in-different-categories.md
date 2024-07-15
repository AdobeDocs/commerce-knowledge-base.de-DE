---
title: "MDVA-36286: Seitenaufbau-Vorschau bricht bei SKU-Positionen in verschiedenen Kategorien ab"
description: Der Patch MDVA-36286 behebt das Problem, bei dem die Vorschau des Seitenaufbaus-Produkt-Widgets unterbrochen wird, wenn dieselbe SKU in Unterkategorien eine andere Position hat. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.23 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: 0f7d2506-569a-4b70-82bf-0f153014c48a
feature: CMS, Categories, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# MDVA-36286: Seitenaufbau-Vorschau bricht bei SKU-Positionen in verschiedenen Kategorien ab

Der Patch MDVA-36286 behebt das Problem, bei dem die Vorschau des Seitenaufbaus-Produkt-Widgets unterbrochen wird, wenn dieselbe SKU in Unterkategorien eine andere Position hat. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.23 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.3.6

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.6 - 2.4.2-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte:</u>

1. Erstellen Sie eine Kategorie mit einigen Produkten.
   ![products_magento_ordered.png](/help/support-tools/patches-available-in-qpt-tool/assets/products_magento_ordered.png)
1. Erstellen Sie eine Unterkategorie mit denselben Produkten, aber unterschiedlichen Positionen.
   ![products_magento_different_position.png](/help/support-tools/patches-available-in-qpt-tool/assets/products_magento_different_position.png)
1. Bearbeiten Sie einen CMS-Seiteninhalt, um über den Seitenaufbau ein Produkt-Widget hinzuzufügen. (Wählen Sie die übergeordnete Kategorie oben aus).
   ![cms_page_magento.png](/help/support-tools/patches-available-in-qpt-tool/assets/cms_page_magento.png)
1. Speichern und warten Sie auf die Inhaltsvorschau.

<u>Erwartete Ergebnisse:</u>

In der Inhaltsvorschau wird das Produkt-Widget angezeigt.

<u>Tatsächliche Ergebnisse:</u>

Fehler wird angezeigt:

*Es tut uns leid, beim Generieren dieses Inhalts ist ein Fehler aufgetreten.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
