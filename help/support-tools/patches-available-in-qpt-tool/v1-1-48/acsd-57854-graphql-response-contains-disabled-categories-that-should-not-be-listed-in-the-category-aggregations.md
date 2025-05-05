---
title: 'ACSD-57854: Die Antwort *GraphQL* enthält deaktivierte Kategorien, die nicht in den Kategorieaggregationen aufgeführt werden sollten'
description: Wenden Sie den Patch ACSD-57854 an, um das Adobe Commerce-Problem zu beheben, bei dem die *GraphQL*-Antwort deaktivierte Kategorien enthält, die nicht in den Kategorieaggregationen aufgeführt werden sollten.
feature: GraphQL
role: Admin, Developer
exl-id: b6130a0f-57bc-4719-99f2-beb630c463c7
source-git-commit: ea6f23a7ce599e24c6b683f82cf08b72b2506020
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57854: Die *GraphQL*-Antwort enthält deaktivierte Kategorien, die nicht in den Kategorieaggregationen aufgeführt werden sollten

Der Patch „ACSD-57854“ behebt das Problem, dass die *GraphQL*-Antwort deaktivierte Kategorien enthält, die nicht in den Kategorieaggregationen aufgeführt werden sollten. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.48 installiert ist. Die Patch-ID ist ACSD-57854. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.5.0 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die *GraphQL*-Antwort enthält deaktivierte Kategorien, die nicht in den Kategorieaggregationen aufgeführt werden sollten.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei Kategorien.
1. Erstellen Sie ein Produkt (Adobe-Produkt testen) und weisen Sie das Produkt beiden Kategorien zu.
1. Deaktivieren Sie eine der erstellten Kategorien.
1. Verwenden Sie Produkte *GraphQL*, um das Produkt zu durchsuchen.
1. Überprüfen Sie die Liste der Produktkategorien in der Antwort *GraphQL*.

<u>Erwartete Ergebnisse</u>:

Die deaktivierten Kategorien werden in der Antwort *GraphQL* nicht aufgeführt.

<u>Tatsächliche Ergebnisse</u>:

Die deaktivierten Kategorien werden in der Antwort der Kategorieaggregation *GraphQL* aufgeführt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
