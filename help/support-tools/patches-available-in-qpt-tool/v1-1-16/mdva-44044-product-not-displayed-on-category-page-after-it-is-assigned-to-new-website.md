---
title: "MDVA-44044: Produkt wird nicht auf der Kategorieseite angezeigt, nachdem es einer neuen Website zugewiesen wurde."
description: Der Patch MDVA-44044 behebt das Problem, dass ein Produkt nicht auf der Kategorieseite angezeigt wird, nachdem es einer neuen Website zugewiesen wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-44044. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
exl-id: e3a179ed-243c-4200-a01a-796657bd31ab
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-44044: Produkt wird nicht auf der Kategorieseite angezeigt, nachdem es einer neuen Website zugewiesen wurde

Der Patch MDVA-44044 behebt das Problem, dass ein Produkt nicht auf der Kategorieseite angezeigt wird, nachdem es einer neuen Website zugewiesen wurde. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-44044. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Produkt wird nicht auf der Kategorieseite angezeigt, nachdem es einer neuen Website zugewiesen wurde.

<u>Zu reproduzierende Schritte</u>:

1. Legen Sie den Indexermodus auf den Zeitplan fest.
1. Erstellen Sie eine sekundäre Website-, Store- und Store-Ansicht.
1. Sekundären Store-Code hinzufügen in `index.php`:

   ```php
   $_SERVER["MAGE_RUN_CODE"]="en_us";
   $_SERVER["MAGE_RUN_TYPE"]="store";
   ```

1. Erstellen Sie eine neue Kategorie.
1. Erstellen Sie ein neues Produkt, das der neu erstellten Kategorie zugewiesen ist. Stellen Sie sicher, dass Sie ihn nur der primären Website zuweisen.
1. Führen Sie den Cron aus.
1. Öffnen Sie die Kategorie in der Storefront.
1. Weisen Sie das Produkt der sekundären Website zu.
1. Führen Sie den Cron erneut aus.

<u>Erwartete Ergebnisse</u>:

Das Produkt wird auf der Kategorieseite nach einem geplanten Indexer angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt wird erst bei vollständiger Neuindizierung auf der Kategorieseite angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
