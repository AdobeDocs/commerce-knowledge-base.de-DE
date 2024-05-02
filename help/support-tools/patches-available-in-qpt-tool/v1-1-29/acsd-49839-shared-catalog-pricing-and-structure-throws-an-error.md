---
title: "ACSD-49839: Freigegebene Katalogpreisstruktur und -struktur lösen einen Fehler aus"
description: Wenden Sie den Patch ACSD-49839 an, um das Adobe Commerce-Problem zu beheben, bei dem die gemeinsame Katalogpreisstruktur und -struktur einen Fehler im Admin auslöst, wenn Produkte einfache oder doppelte Anführungszeichen in der SKU aufweisen.
exl-id: 4c477ae8-602b-452e-83f0-b72a29547ef9
feature: Admin Workspace, Catalog Management, Categories
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-49839: Gemeinsame Katalogpreisstruktur und -struktur lösen einen Fehler aus

Der Patch ACSD-49839 behebt das Problem, dass die gemeinsame Katalogpreisstruktur und -struktur einen Fehler im Admin ausgibt, wenn Produkte einfache oder doppelte Anführungszeichen in der SKU haben. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 ist installiert. Die Patch-ID lautet ACSD-49839. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die freigegebene Katalogpreisstruktur und -struktur gibt im Administrator einen Fehler aus, wenn Produkte einfache oder doppelte Anführungszeichen in der SKU aufweisen.

<u>Zu reproduzierende Schritte</u>:

1. Legen Sie einige Produkt-SKUs mit einem Sonderzeichen fest, d. h. doppelte Anführungszeichen wie:
   *[Product&quot;12, Product&quot;14, Product&quot;15]*.
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Add Shared Catalog]** (z. B.*[Freigegebenen Katalog testen]*).
1. Alle zuweisen **[!UICONTROL Products and Categories]** > **[!UICONTROL Generate Catalog]** > **[!UICONTROL Save]**.
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Test Shared Catalog]** > **[!UICONTROL Action]** > **[!UICONTROL Set Pricing and Structure]**.
1. Mark *[!UICONTROL Root Catalog]* zur Auswahl aller Kategorien und Produkte.
1. Beobachten Sie die AJAX Anforderungen im Netzwerkbereich.

<u>Erwartete Ergebnisse</u>:

Die gemeinsame Katalogpreisstruktur und -struktur gibt keinen Fehler im Admin aus, wenn Produkte einfache oder doppelte Anführungszeichen in der SKU haben.

<u>Tatsächliche Ergebnisse</u>:

Die gemeinsame Katalogpreisstruktur und -struktur gibt im Admin einen Fehler aus, wenn Produkte einfache oder doppelte Anführungszeichen in der SKU haben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
