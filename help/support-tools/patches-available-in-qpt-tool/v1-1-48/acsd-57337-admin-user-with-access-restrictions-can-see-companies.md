---
title: "ACSD-57337: Admin-Benutzer mit Zugriffsbeschränkungen konnten alle Unternehmen im *Unternehmensnetz* anzeigen."
description: Wenden Sie den Patch ACSD-57337 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Admin-Benutzer mit Zugriffsbeschränkungen auf bestimmte Websites Unternehmen von allen Websites im *Unternehmen*-Raster aus anzeigen konnte.
feature: Companies, B2B, Configuration
role: Admin, Developer
source-git-commit: a02c80006f1c8a434fe17322f0c6cee25f086396
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-57337: Admin-Benutzer mit Zugriffsbeschränkungen könnten alle Unternehmen in der *Unternehmen* grid

Der Patch ACSD-57337 behebt das Problem, dass ein Administrator mit Zugriffsbeschränkungen für bestimmte Websites Unternehmen von allen Websites in der *Unternehmen* Gitter. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 ist installiert. Die Patch-ID ist ACSD-57337. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.5.0 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein Admin-Benutzer mit Zugriffsbeschränkungen für bestimmte Websites könnte Unternehmen von allen Websites in der *Unternehmen* Gitter.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine zusätzliche Website, einen Store und eine Storeübersicht.
1. Erstellen Sie einige Unternehmen, die verschiedenen Websites zugewiesen sind.
1. Erstellen Sie eine Admin-Benutzerrolle und legen Sie den Rollenbereich auf die erstellte Website fest.
1. Erstellen Sie einen Administrator und weisen Sie ihn der erstellten Rolle zu.
1. Melden Sie sich mit einem neuen Administrator an.
1. Öffnen **[!UICONTROL Customers]** > **[!UICONTROL Companies]** und beobachten Sie die Liste der Unternehmen.

<u>Erwartete Ergebnisse</u>:

Die Unternehmen, die der zusätzlichen Website zugewiesen wurden, sind im *Unternehmen* Gitter.

<u>Tatsächliche Ergebnisse</u>:

Alle Unternehmen sind im *Unternehmen* Gitter.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.