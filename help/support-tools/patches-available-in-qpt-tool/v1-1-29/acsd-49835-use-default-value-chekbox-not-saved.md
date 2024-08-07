---
title: 'ACSD-49835: [!UICONTROL Use Default Value] Kontrollkästchen wird nicht gespeichert.'
description: Wenden Sie den Patch ACSD-49835 an, um das Adobe Commerce-Problem zu beheben, bei dem das Kontrollkästchen [!UICONTROL Use Default Value] nicht ordnungsgemäß auf einer Store-Ebene für ein Attribut mit Mehrfachauswahl gespeichert wird.
exl-id: 84270551-c8a9-4b08-a055-ffdcc538c33d
feature: Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-49835: [!UICONTROL Use Default Value] Kontrollkästchen wird nicht gespeichert

Der Patch ACSD-49835 behebt das Problem, dass das Kontrollkästchen [!UICONTROL Use Default Value] nicht ordnungsgemäß auf einer Store-Ebene für ein Attribut mit Mehrfachauswahl gespeichert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 installiert ist. Die Patch-ID lautet ACSD-49835. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Kontrollkästchen [!UICONTROL Use Default Value] wird für ein Attribut mit Mehrfachauswahl nicht ordnungsgemäß auf Store-Ebene gespeichert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine **[!UICONTROL Multiple-select Attribute]** in **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** und fügen Sie sie einem Attributsatz hinzu.
1. Gehen Sie zu einer **[!UICONTROL Product]** und speichern Sie **[!UICONTROL Values]** in **[!UICONTROL All Store Views (Default Scope)]**.
1. Wechseln Sie zu einem bestimmten **[!UICONTROL Store View Scope]** und speichern Sie das Produkt.
1. Gehen Sie zu **[!UICONTROL Store View Scope]** und aktivieren Sie das Kontrollkästchen **[!UICONTROL Use Default Value]** .

<u>Erwartete Ergebnisse</u>:

Attributwerte mit Mehrfachauswahl werden beim Aktivieren des Kontrollkästchens [!UICONTROL Use Default Value] im Feld [!UICONTROL Store View Scope] ordnungsgemäß gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Attributwerte mit Mehrfachauswahl werden beim Aktivieren des Kontrollkästchens [!UICONTROL Use Default Value] im Feld [!UICONTROL Store View Scope] nicht ordnungsgemäß gespeichert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
