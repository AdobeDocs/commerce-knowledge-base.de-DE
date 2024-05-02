---
title: '"ACSD-49835: [!UICONTROL Use Default Value] Kontrollkästchen nicht gespeichert'
description: Wenden Sie den Patch ACSD-49835 an, um das Adobe Commerce-Problem zu beheben, bei dem das [!UICONTROL Use Default Value] nicht korrekt auf einer Store-Ebene für ein Attribut mit Mehrfachauswahl gespeichert.
exl-id: 84270551-c8a9-4b08-a055-ffdcc538c33d
feature: Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-49835: [!UICONTROL Use Default Value] nicht gespeichert

Der Patch ACSD-49835 behebt das Problem, bei dem das [!UICONTROL Use Default Value] nicht korrekt auf einer Store-Ebene für ein Attribut mit Mehrfachauswahl gespeichert. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 ist installiert. Die Patch-ID lautet ACSD-49835. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die [!UICONTROL Use Default Value] nicht korrekt auf einer Store-Ebene für ein Attribut mit Mehrfachauswahl gespeichert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine **[!UICONTROL Multiple-select Attribute]** in **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** und fügen Sie sie einem Attributsatz hinzu.
1. Gehen Sie zu einem **[!UICONTROL Product]** und speichern **[!UICONTROL Values]** in **[!UICONTROL All Store Views (Default Scope)]**.
1. Gehen Sie zu einem bestimmten **[!UICONTROL Store View Scope]** und speichern Sie das Produkt.
1. Navigieren Sie zu **[!UICONTROL Store View Scope]** und überprüfen Sie die **[!UICONTROL Use Default Value]** aktivieren.

<u>Erwartete Ergebnisse</u>:

Attributwerte mit Mehrfachauswahl werden beim Überprüfen der [!UICONTROL Use Default Value] im [!UICONTROL Store View Scope].

<u>Tatsächliche Ergebnisse</u>:

Attributwerte mit Mehrfachauswahl werden beim Überprüfen der Variablen [!UICONTROL Use Default Value] im [!UICONTROL Store View Scope].

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
