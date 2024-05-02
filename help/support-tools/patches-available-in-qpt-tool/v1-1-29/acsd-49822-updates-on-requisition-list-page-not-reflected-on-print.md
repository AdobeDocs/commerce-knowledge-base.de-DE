---
title: "ACSD-49822: Aktualisierungen auf der Anforderungslistenseite werden nicht in der Liste der Druckanforderungen angezeigt."
description: Wenden Sie den Patch ACSD-49822 an, um das Adobe Commerce-Problem zu beheben, bei dem Aktualisierungen auf der Anforderungslistenseite nicht in der Druckanforderungsliste angezeigt werden.
exl-id: 584e3fcd-9153-41aa-8857-cf1fa41269c9
feature: Admin Workspace, B2B
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-49822: Aktualisierungen in der Anforderungsliste werden nicht in der Liste der Druckanforderungen angezeigt

Der Patch ACSD-49822 behebt das Problem, dass Aktualisierungen auf der Anforderungslistenseite nicht in der Liste der Druckanforderungen angezeigt werden. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 ist installiert. Die Patch-ID lautet ACSD-49822. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Aktualisierungen auf der Anforderungslistenseite werden nicht in der Liste der Druckanforderungen angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie die Anforderungsliste, indem Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[B2B-Funktionen]**.
1. Erstellen Sie ein Produkt.
1. Melden Sie sich als Kunde an und fügen Sie der Anforderungsliste zwei Produkte hinzu.
1. Navigieren Sie zu **[!UICONTROL My Account]** > **[!UICONTROL My Requisition Lists]**.
1. Eine Anforderungsliste anzeigen.
1. Klicks **[!UICONTROL Print]** in der oberen rechten Ecke.
1. Schließen Sie das Druckfenster und die Seite mit der Liste der Druckanforderungen.
1. Löschen Sie ein Element in der Liste oder aktualisieren Sie eine Menge eines Elements, und versuchen Sie erneut, es zu drucken.
1. Sie werden feststellen, dass die Elemente nicht im Druckfenster aktualisiert werden.
1. Schließen Sie das Druckfenster.
1. Sie werden feststellen, dass die Elemente auf der Druckseite der Anforderungsliste nicht aktualisiert werden.

<u>Erwartete Ergebnisse</u>:

Die zu druckende Liste wird nach jeder Änderung aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

Aktualisierungen werden nicht auf der Druckseite der Anforderungsliste angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
