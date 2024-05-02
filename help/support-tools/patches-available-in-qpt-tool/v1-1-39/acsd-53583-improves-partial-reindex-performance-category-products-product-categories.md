---
title: '"ACSD-53583: Verbessern der partiellen Neuindizierungsleistung für [!UICONTROL Category Products] und [!UICONTROL Product Categories] Indexer'
description: Wenden Sie den Patch ACSD-53585 an, um die partielle Neuindizierungsleistung für Indizes für Kategorie-Produkte und Produktkategorien zu verbessern.
feature: Products, Categories
role: Admin, Developer
exl-id: 1c8f7df3-379f-42d6-8b41-286d34f725d2
source-git-commit: 29c2918ccae6404f6ae87d360ac16b149de5dd0d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-53583: Verbessern der partiellen Neuindizierungsleistung für Indexer für Kategorie-Produkte und Produktkategorien

Der Patch ACSD-53583 verbessert die partielle Neuindizierungsleistung von *Kategorieprodukte* und *Produktkategorien* Indexer. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.39 ist installiert. Die Patch-ID ist ACSD-53583. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p3
* Nicht kompatibel mit [!DNL Live Search] -Modul. Um diesen Patch auf [!DNL Live Search] Installation, fordern Sie bitte einen zusätzlichen ACSD-55719 Patch an.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die partielle Neuindizierung dauert länger als die vollständige Neuindizierung.

<u>Zu reproduzierende Schritte</u>:

1. Alle Indexer in *Nach Zeitplan aktualisieren*.
1. Generieren Sie Daten mit der [!DNL Performance Toolkit] (mittleres Profil).
1. Nehmen Sie Änderungen an allen Produkten und Kategorien vor, damit sie im Index-Rückstand sind und alle Indizes inaktiv sind.
1. Teilweise Neuindizierung durchführen für *Kategorieprodukte* und *Produktkategorien* Indexer.

<u>Erwartete Ergebnisse</u>:

Teilweise wird die Neuindizierung einmal pro Produkt aufgerufen und nimmt fast dieselbe Zeit ein wie die vollständige Neuindizierung, da alle Produkte und Kategorien geändert wurden.

<u>Tatsächliche Ergebnisse</u>:

Eine partielle Neuindizierung wird oft pro Produkt aufgerufen und dauert länger als eine vollständige Neuindizierung.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
