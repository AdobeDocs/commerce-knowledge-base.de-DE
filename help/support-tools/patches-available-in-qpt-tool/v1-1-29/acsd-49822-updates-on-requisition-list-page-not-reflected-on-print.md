---
title: 'ACSD-49822: Aktualisierungen auf der Seite der Anforderungsliste werden nicht in der Druckanforderungsliste angezeigt'
description: Wenden Sie den Patch ACSD-49822 an, um das Adobe Commerce-Problem zu beheben, bei dem Aktualisierungen auf der Seite „Anforderungsliste“ nicht in der Druckanforderungsliste angezeigt werden.
exl-id: 584e3fcd-9153-41aa-8857-cf1fa41269c9
feature: Admin Workspace, B2B
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-49822: Aktualisierungen in der Anforderungsliste werden nicht in der Druckanforderungsliste angezeigt

Mit dem Patch ACSD-49822 wird das Problem behoben, dass Aktualisierungen auf der Seite „Anforderungsliste“ nicht in der Druckanforderungsliste angezeigt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 installiert ist. Die Patch-ID ist ACSD-49822. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Aktualisierungen auf der Seite „Anforderungsliste“ werden nicht in der Druckanforderungsliste angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie die Anforderungsliste, indem Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[B2B-Funktionen]** navigieren.
1. Erstellen Sie ein Produkt.
1. Melden Sie sich als Kunde an und fügen Sie der Anforderungsliste zwei Produkte hinzu.
1. Navigieren Sie zu **[!UICONTROL My Account]** > **[!UICONTROL My Requisition Lists]**.
1. Anforderungsliste anzeigen.
1. Klicken Sie oben rechts auf **[!UICONTROL Print]** .
1. Schließen Sie das Druckfenster und drucken Sie die Seite „Anforderungsliste“.
1. Löschen Sie ein Element in der Liste oder aktualisieren Sie eine Menge eines Elements und versuchen Sie erneut, es zu drucken.
1. Sie werden feststellen, dass die Elemente im Druckfenster nicht aktualisiert werden.
1. Schließen Sie das Druckfenster.
1. Sie werden feststellen, dass die Artikel auf der Druckseite der Anforderungsliste nicht aktualisiert werden.

<u>Erwartete Ergebnisse</u>:

Die zu druckende Liste wird nach jeder Änderung aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

Aktualisierungen werden nicht auf der Druckseite der Anforderungsliste angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
