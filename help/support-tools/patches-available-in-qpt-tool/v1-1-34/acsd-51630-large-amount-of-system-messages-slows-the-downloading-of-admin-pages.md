---
title: 'ACSD-51630: Zahlreiche Systemmeldungen verlangsamen den Download von Admin-Seiten'
description: Wenden Sie den ACSD-51630 Patch an, um das Leistungsproblem von Adobe Commerce zu beheben, bei dem das Herunterladen von Admin-Seiten durch eine große Anzahl von Systemmeldungen verlangsamt wird.
feature: Admin Workspace, System
role: Admin
exl-id: 28f85199-625e-4299-bbca-8d2fc75df602
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# ACSD-51630: Zahlreiche Systemmeldungen verlangsamen den Download von Admin-Seiten

Mit dem Patch ACSD-51630 wird das Leistungsproblem behoben, bei dem das Herunterladen von Admin-Seiten durch eine große Anzahl von Systemmeldungen verlangsamt wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.34 installiert ist. Die Patch-ID ist ACSD-51630. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 &lt; 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Zahlreiche Systemmeldungen verlangsamen den Download von Admin-Seiten

<u>Schritte zur Reproduktion</u>:

1. Stellen Sie eine große Anzahl von Anfragen (~50.000) an DELETE `/rest/async/v1/products/ {sku}`.
1. Rufen Sie eine beliebige **Admin-Seite** auf.

<u>Erwartete Ergebnisse</u>:

Seite wird in geeigneter Zeit geladen. Es sollten nur angezeigte Nachrichten geladen werden.

<u>Tatsächliche Ergebnisse</u>:

Das Laden der Seite dauert zu lange. Alle vorhandenen Nachrichten werden aus der Datenbank geladen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
