---
title: '"ACSD-45049: Kundenattributeinstellung "Ist erforderlich"funktioniert nicht gemäß Website-Umfang in Admin"'
description: Wenden Sie den Patch ACSD-45049 an, um das Adobe Commerce-Problem zu beheben, bei dem das Kundenattribut "[!UICONTROL Is required]" gemäß dem Website-Umfang in Admin nicht ordnungsgemäß überschrieben wird.
feature: Attributes, Customers
role: Admin, Developer
source-git-commit: 16e7c9e4e4bbbc62db0671016bce85ecb6414622
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-45049: Kundenattributeinstellung *[!UICONTROL Is required]* funktioniert nicht gemäß Website-Umfang in Admin

Der Patch ACSD-45049 behebt das Problem, dass die Kundenattributeinstellung *[!UICONTROL Is required]* gemäß dem Website-Umfang in Admin nicht ordnungsgemäß funktioniert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.50 installiert ist. Die Patch-ID ist ACSD-45049. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p7 und 2.4.5 - 2.4.5-p9

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Kundenattributeinstellung *[!UICONTROL Is required]* funktioniert nicht ordnungsgemäß gemäß dem Website-Umfang in Admin.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie zwei Websites.
1. Öffnen Sie **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer attribute]**.
1. Erstellen Sie ein neues Attribut, legen Sie **[!UICONTROL Is value required]** = *Nein* fest.
1. Wechseln Sie zur Standardwebsite und ändern Sie **[!UICONTROL Is value required]** = *Ja*. Die andere Website hat den Standardwert.
1. Erstellen Sie einen neuen Kunden von Admin für die nicht standardmäßige Website.

<u>Erwartete Ergebnisse</u>:

Das -Attribut ist für die nicht standardmäßige Website nicht erforderlich.

<u>Tatsächliche Ergebnisse</u>:

* Das Attribut ist für die nicht standardmäßige Website erforderlich, wenn ein Kunde in Admin erstellt wird.
* Das -Attribut ist für die nicht standardmäßige Website nicht erforderlich, wenn ein Kunde auf der Storefront registriert wird.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
