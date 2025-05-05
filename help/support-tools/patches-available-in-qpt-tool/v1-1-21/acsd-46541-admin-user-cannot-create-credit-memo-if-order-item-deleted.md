---
title: 'ACSD-46541: Ein Administrator kann keine Gutschrift erstellen, wenn ein Bestellartikel gelöscht wird'
description: Wenden Sie den ACSD-46541 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem Sie nach dem Löschen eines Produkts keine Gutschrift in Adobe Commerce Admin erstellen können.
exl-id: ff3f8f21-76c1-41b5-bf02-349403a46fc1
feature: Admin Workspace, Orders, Returns
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46541: Ein Administrator kann keine Gutschrift erstellen, wenn ein Bestellartikel gelöscht wird

Der Patch ACSD-46541 behebt das Problem, dass ein Administrator keine Gutschrift erstellen kann, wenn ein Bestellartikel gelöscht wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 installiert ist. Die Patch-ID ist ACSD-46541. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Nachdem ein Produkt gelöscht wurde, können Sie keine Gutschrift mehr in Commerce Admin erstellen.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich beim Commerce Admin an.
1. Erstellen Sie eine Bestellung.
1. Rechnung der Bestellung.
1. Löschen Sie das Produkt aus der Bestellung.
1. Klicken Sie auf den Link **[!UICONTROL Credit Memo]** auf der Seite zur Bearbeitung der Bestellung.
1. Klicken Sie auf **[!UICONTROL Refund Offline]** , um eine Gutschrift zu erstellen.

<u>Erwartete Ergebnisse</u>:

Eine Gutschrift wurde erfolgreich erstellt.

<u>Tatsächliche Ergebnisse</u>:

Die _Produkte mit angeforderten SKUs wurden nicht gefunden: SKU001_ Fehleranzeigen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
