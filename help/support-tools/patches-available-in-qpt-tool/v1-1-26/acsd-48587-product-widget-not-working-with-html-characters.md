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

Der Patch ACSD-48587 behebt das Problem, dass HTML-Sonderzeichen in den Übereinstimmungsregeln für Produkte-Widgets verhindern, dass sie übereinstimmende Produkte anzeigen. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 installiert ist. Die Patch-ID lautet ACSD-48587. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Produkt-Widget funktioniert nicht mit SKUs, die *&quot;&amp;&quot;* -Symbole enthalten.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Produkt, das *&quot;&amp;&quot;* in der SKU enthält (z. B. s000&amp;01).
1. Bearbeiten Sie den Inhalt einer CMS-Seite im *Seitenaufbau*.
1. Hinzufügen eines Produkt-Widgets.
1. Bearbeiten Sie das Widget und legen Sie **[!UICONTROL Select Products by]** = **[!UICONTROL SKU]** fest.
1. Geben Sie die SKU ein, die *&quot;&amp;&quot;* enthält, in das Feld Produkt-SKUs.
1. Speichern Sie den Inhalt und die CMS-Seite.
1. Überprüfen Sie den Inhalt der *CMS-Seite* für die *Seitenaufbau-Vorschau* und die Produkt-Storefront.

<u>Erwartete Ergebnisse</u>:

Das Produkt mit &quot;*&quot;&amp;&quot;* in der SKU wird in der Seitenaufbau-Vorschau und auf der Storefront angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt mit &quot;*&quot;&amp;&quot;* in der SKU wird nicht in der Seitenaufbau-Vorschau angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
