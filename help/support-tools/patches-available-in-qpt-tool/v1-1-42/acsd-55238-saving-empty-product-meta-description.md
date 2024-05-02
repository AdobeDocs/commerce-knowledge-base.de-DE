---
title: "ACSD-55238: Save the empty product meta description"
description: Wenden Sie den Patch ACSD-55238 an, um das Adobe Commerce-Problem zu beheben, bei dem eine Produktbeschreibung mit HTML-Code, der von generiert wurde, [!DNL Page Builder] oder ein anderer HTML-Editor immer in der Meta-Beschreibung angezeigt wird und es gibt keine Möglichkeit, ihn auf "Leer"festzulegen.
feature: Products, Page Builder, Page Content
role: Admin, Developer
exl-id: 250026c3-925d-4a62-9855-d892c86d3d24
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-55238: Speichern der leeren Produktmeta-Beschreibung

Der Patch ACSD-55238 behebt das Problem, dass eine Produktbeschreibung, die von einem HTML-Editor generierten HTML-Code enthält, immer in der Meta-Beschreibung angezeigt wird. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 ist installiert. Die Patch-ID ist ACSD-55238. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eine Produktbeschreibung mit HTML-Code, der von [!DNL Page Builder] oder ein anderer HTML-Editor immer in der Meta-Beschreibung angezeigt wird und es gibt keine Möglichkeit, ihn auf &quot;Leer&quot;festzulegen.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Block]** und erstellen Sie einen neuen Baustein mit beliebigen Inhalten.
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product]** und erstellen Sie ein neues Produkt. Legen Sie die Meta-Beschreibung auf &quot;leer&quot;fest.
1. Fügen Sie den oben erstellten Baustein mit *[!DNL Page Builder]* im *[!UICONTROL Content]* und speichern Sie das Produkt.
1. Öffnen Sie das Produkt auf der Storefront und überprüfen Sie das doc -Element. `meta name = "description"`.

<u>Erwartete Ergebnisse</u>:

Die Meta-Beschreibung ist leer.

<u>Tatsächliche Ergebnisse</u>:

Wenn die Beschreibung eines Produkts einen Baustein enthält, wird dieser für die Beschreibung der Produktmeta verwendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
