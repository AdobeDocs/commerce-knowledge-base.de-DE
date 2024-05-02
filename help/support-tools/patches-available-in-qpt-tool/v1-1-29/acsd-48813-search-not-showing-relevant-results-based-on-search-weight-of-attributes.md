---
title: "ACSD-48813: Suche zeigt keine relevanten Ergebnisse basierend auf der Suchgewichtung von Attributen an."
description: Wenden Sie den Patch ACSD-48813 an, um das Adobe Commerce-Problem zu beheben, bei dem die Suche keine relevanten Ergebnisse basierend auf der Suchgewichtung der Attribute anzeigt.
exl-id: 089e3ab3-0dfa-4f81-85c7-f6060f326d97
feature: Admin Workspace, Attributes, Search
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-48813: Suche zeigt keine relevanten Ergebnisse basierend auf der Suchgewichtung von Attributen an

Der Patch ACSD-48813 behebt das Problem, dass die Suche keine relevanten Ergebnisse basierend auf der Suchgewichtung der Attribute anzeigt. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 ist installiert. Die Patch-ID lautet ACSD-48813. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Suche zeigt keine relevanten Ergebnisse basierend auf der Suchgewichtung der Attribute an.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Adobe Commerce mit Beispieldaten.
1. Stellen Sie die Suchmaschine auf [!DNL Elasticsearch].
1. Melden Sie sich als Administrator an.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Products]**.
1. Öffnen Sie die *name* -Attribut.
1. Storefront öffnen *[!UICONTROL Properties]* Registerkarte.
1. Auswählen [!UICONTROL Search Weight] = *10* aus dem Dropdown-Wert aus.
1. Klicks **[!UICONTROL Save Attribute]**.
1. Öffnen Sie nun die Storefront und suchen Sie nach dem Wort *Zurück*.

<u>Erwartete Ergebnisse</u>:

Backpack-Produkte werden oben in den Suchergebnissen zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

Backpack-Produkte werden mitten in den Suchergebnissen zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
