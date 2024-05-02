---
title: "ACSD-49497: Auftragsabwicklung nach dem Versand und Teilerstattung"
description: Wenden Sie den Patch ACSD-49497 an, um das Adobe Commerce-Problem zu beheben, bei dem der Auftragsstatus nach dem Versand als Verarbeitung beibehalten wird und eine teilweise Rückerstattung erfolgt.
exl-id: d195bcf4-bb8b-4373-8aad-a5b953b07443
feature: Admin Workspace, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-49497: Auftragsabwicklung nach dem Versand und Teilrückerstattung

Der Patch ACSD-49497 behebt das Problem, dass der Auftragsstatus nach dem Versand als Verarbeitung gilt und eine teilweise Rückerstattung erfolgt. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 ist installiert. Die Patch-ID lautet ACSD-49497. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Status einer neuen Bestellung verbleibt im *[!UICONTROL Processing]* Angabe auch nach dem Versand und Anwendung einer teilweisen Erstattung.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Bestellung mit mehreren Elementen.
1. Von **[!UICONTROL Admin]**, erstellen Sie eine Rechnung für die Bestellung.
1. Von **[!UICONTROL Admin]**, erstellen Sie ein Kreditmemo und erstatten Sie einen Artikel nur teilweise zurück.
1. Von **[!UICONTROL Admin]**, fordern Sie den Versand für die verbleibenden Elemente in der Bestellung an.
1. Beobachten Sie den Bestellstatus.

<u>Erwartete Ergebnisse</u>:

Der Status der Bestellung sollte *[!UICONTROL Complete]*.

<u>Tatsächliche Ergebnisse</u>:

Der Status der Anordnung bleibt erhalten *[!UICONTROL Processing]*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
