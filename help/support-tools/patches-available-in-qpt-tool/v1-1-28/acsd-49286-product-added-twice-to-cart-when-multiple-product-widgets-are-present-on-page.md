---
title: "ACSD-49286: Produkt zweimal zum Warenkorb hinzugefügt, wenn mehrere Produkt-Widgets vorhanden sind"
description: Wenden Sie den Patch ACSD-49286 an, um das Adobe Commerce-Problem zu beheben, bei dem das Produkt zweimal zum Warenkorb hinzugefügt wird, wenn mehrere Produkt-Widgets auf der Seite vorhanden sind.
exl-id: b1764943-945d-4ef9-9bbe-3f3c8383b5b1
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49286: Produkt zweimal zum Warenkorb hinzugefügt, wenn mehrere Produkt-Widgets vorhanden sind

Der Patch ACSD-49286 behebt das Problem, dass das Produkt zweimal zum Warenkorb hinzugefügt wird, wenn mehrere Produkt-Widgets auf der Seite vorhanden sind. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 ist installiert. Die Patch-ID lautet ACSD-49286. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Produkt wird einem Warenkorb zweimal hinzugefügt, wenn auf der Seite mehrere Produkt-Widgets vorhanden sind.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Administrator an und wechseln Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Home Page]**
1. Klicken Sie im Inhaltsbereich auf **[!UICONTROL Edit]** using [!DNL Page Builder].
1. Fügen Sie zwei Zeilenelemente zu **[!UICONTROL Content]**.
1. Fügen Sie Produkte in beide Zeilenelemente ein.
1. Legen Sie in der ersten Zeile das Produkterscheinungsbild als [!UICONTROL Product Grid] und wählen Sie eine beliebige Kategorie aus, die angezeigt werden soll.
1. Legen Sie in der zweiten Zeile das Produkterscheinungsbild auf [!UICONTROL Product Carousel] und wählen Sie eine andere Kategorie aus, die angezeigt werden soll.
1. Gehen Sie zur Storefront **[!UICONTROL Home Page]** und fügen Sie ein Produkt aus dem Produktraster hinzu.
1. Ein weiteres Produkt aus [!UICONTROL Product Carousel].

<u>Erwartete Ergebnisse</u>:

Die Produktmenge sollte sich nach dem Hinzufügen eines Produkts zum Warenkorb nicht verdoppeln [!UICONTROL Product Grid].

<u>Tatsächliche Ergebnisse</u>:

Die Produktmenge verdoppelt sich nach dem Hinzufügen eines Produkts zum Warenkorb von [!UICONTROL Product Grid].

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch. 

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
