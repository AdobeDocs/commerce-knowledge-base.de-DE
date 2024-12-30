---
title: 'ACSD-52815: Eingabefeld für das Mengenfeld einer nicht standardmäßigen Quelle unterstützt nur bis zu 6 Stellen'
description: Wenden Sie den Patch ACSD-52815 an, um das Leistungsproblem von Adobe Commerce zu beheben, bei dem das Eingabefeld für das Mengenfeld einer nicht standardmäßigen Quelle nur bis zu 6 Stellen unterstützt, im Gegensatz zu 8 für einen Standardbestand.
feature: Inventory, Products
role: Admin
exl-id: 44fda5ef-cb8a-481a-9112-f36d886ae3db
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-52815: Eingabefeld für das Mengenfeld einer nicht standardmäßigen Quelle unterstützt nur bis zu 6 Stellen

Der Patch ACSD-52815 behebt das Problem, dass das Eingabefeld für das Mengenfeld einer nicht standardmäßigen Quelle nur bis zu 6 Stellen unterstützt, im Gegensatz zu 8 für einen Standardbestand. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-52815. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Eingabefeld für das Mengenfeld einer nicht standardmäßigen Quelle unterstützt nur bis zu 6 Stellen, im Gegensatz zu 8 für einen Standardbestand.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein neues Lager und eine neue Quelle.
1. Erstellen Sie ein Produkt mit einem neuen Quellbestand von 123.
1. Überprüfen Sie die verkaufsfähige Menge (123).
1. Quellmenge auf 12345678 aktualisieren.
1. Die zu verkaufende Menge erneut überprüfen.

<u>Erwartete Ergebnisse</u>:

Die verkaufbare Menge zeigt die richtige Menge an.

<u>Tatsächliche Ergebnisse</u>:

Die verkaufsfähige Menge beträgt 999999.9999.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
