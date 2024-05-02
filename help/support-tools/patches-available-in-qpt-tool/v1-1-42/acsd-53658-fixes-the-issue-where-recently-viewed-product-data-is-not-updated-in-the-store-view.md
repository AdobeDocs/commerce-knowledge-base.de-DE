---
title: '"ACSD-53658: **[!UICONTROL Recently Viewed Product]** Daten werden in der Store-Ansicht nicht ordnungsgemäß aktualisiert.'
description: Wenden Sie den Patch ACSD-53658 an, um das Adobe Commerce-Problem zu beheben, bei dem **[!UICONTROL Recently Viewed Product]** Daten werden in der Store-Ansicht nicht ordnungsgemäß aktualisiert.
feature: CMS, Personalization
role: Admin, Developer
exl-id: 4086dcee-37e5-4393-9048-ce19a2d248e9
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-53658: **[!UICONTROL Recently Viewed Product]** Daten, die in der Store-Ansicht nicht ordnungsgemäß aktualisiert wurden

Der Patch ACSD-53658 behebt das Problem, bei dem **[!UICONTROL Recently Viewed Product]** -Daten werden in der Store-Ansicht nicht ordnungsgemäß aktualisiert. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 ist installiert. Die Patch-ID ist ACSD-53658. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die **[!UICONTROL Recently Viewed Product]** -Daten werden in der Store-Ansicht nicht ordnungsgemäß aktualisiert.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Admin-Bedienfeld an.
1. Erstellen Sie eine zweite Store-Ansicht für die Standardwebsite.
1. Erstellen Sie ein einfaches Produkt.
1. Legen Sie einen anderen Produktnamen für die neue Store-Ansicht fest.
1. Erstellen Sie eine **[!UICONTROL Recently Viewed Product]** Widget.
1. Konfigurieren Sie dieses Widget für die Anzeige auf der Startseite.
1. Öffnen Sie die Produktseite in der Storefront in der standardmäßigen Store-Ansicht.
1. Öffnen Sie die Startseite.
1. Wechseln Sie mithilfe des Store-Switchers zur zweiten Store-Ansicht.

<u>Erwartete Ergebnisse</u>:

Der Produktname wird im Widget aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

Der Produktname wird im Widget nicht aktualisiert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
