---
title: "ACSD-48587: Produkt-Widget funktioniert nicht mit SKUs, die HTML-Zeichen enthalten."
description: Wenden Sie den Patch ACSD-48587 an, um das Adobe Commerce-Problem zu beheben, bei dem HTML-Sonderzeichen in den Übereinstimmungsregeln für Produkte-Widgets verhindern, dass sie übereinstimmende Produkte anzeigen.
exl-id: 9f8f436c-f3ef-4510-a941-12f701e7524e
feature: Admin Workspace, CMS, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48587: Produkt-Widget funktioniert nicht mit SKUs mit HTML-Zeichen

Der Patch ACSD-48587 behebt das Problem, dass HTML-Sonderzeichen in den Übereinstimmungsregeln für Produkte-Widgets verhindern, dass sie übereinstimmende Produkte anzeigen. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 installiert ist. Die Patch-ID lautet ACSD-48587. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Produkt-Widget funktioniert nicht mit SKUs, die *&quot;&amp;&quot;* -Symbole.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Produkt, das *&quot;&amp;&quot;* in der SKU (z. B. s000&amp;01).
1. Bearbeiten Sie den Inhalt einer CMS-Seite auf der *Page Builder*.
1. Hinzufügen eines Produkt-Widgets.
1. Widget bearbeiten und festlegen **[!UICONTROL Select Products by]** = **[!UICONTROL SKU]**.
1. Geben Sie die SKU ein, die enthält *&quot;&amp;&quot;* im Feld Produkt-SKUs .
1. Speichern Sie den Inhalt und die CMS-Seite.
1. Überprüfen Sie die *CMS-Seite* Inhalt für *Page Builder-Vorschau* und Produktspeicher.

<u>Erwartete Ergebnisse</u>:

Mit *&quot;&amp;&quot;* in der SKU wird in der Page Builder-Vorschau und auf der Storefront angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Mit *&quot;&amp;&quot;* in der SKU wird nicht in der Seitenaufbau-Vorschau angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
