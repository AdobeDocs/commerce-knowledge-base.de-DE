---
title: 'ACSD-58054: API-Token-Generierung für inaktive Kunden'
description: Wenden Sie den ACSD-58054 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem Kunden-Token für inaktive Kunden über die -API generiert werden können.
feature: Customers, API Mesh
role: Admin, Developer
exl-id: 8c95ff8e-94b1-453a-9bb8-388612b6408f
source-git-commit: 06f751e43ef825c0eb29cb9b42eb41f07c308625
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# ACSD-58054: API-Token-Generierung für inaktive Kunden

Mit dem Patch ACSD-58054 wird das Problem behoben, dass es möglich ist, Kunden-Token für inaktive Kunden über die -API zu generieren. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 installiert ist. Die Patch-ID ist ACSD-58054. Beachten Sie, dass das Problem voraussichtlich in B2B 1.5.1 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p9

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Inaktive Generierung von Kunden-Token über API.

<u>Voraussetzungen</u>:

Die B2B-Module werden installiert.

<u>Schritte zur Reproduktion</u>:

1. Kundenkonto erstellen.
1. Erstellen eines Kunden-Tokens mit der -API.
1. Navigieren Sie zum Backend und deaktivieren Sie das Kundenkonto.
1. Versuchen Sie erneut, ein Kunden-Token zu generieren.

<u>Erwartete Ergebnisse</u>:

Es wird kein Token generiert.

<u>Tatsächliche Ergebnisse</u>:

Ein Token wird generiert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
