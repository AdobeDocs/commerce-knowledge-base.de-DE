---
title: "ACSD-51819: Platzierung mehrerer Bestellungen mit einer einzigen Anführungszeichen-ID"
description: Wenden Sie den Patch ACSD-51819 an, um das Adobe Commerce-Problem zu beheben, bei dem mehrere Bestellungen über dieselbe Angebots-ID platziert werden können.
feature: Orders, Checkout
role: Admin, Developer
exl-id: f217de21-2914-4b84-b596-e9e763669941
source-git-commit: 6fa7182a807147a00ad750966cd839ec18ffe0c7
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51819: Mehrere Bestellungen mit einer einzigen Anführungszeichen-ID platzieren

Der Patch ACSD-51819 behebt das Problem, dass mehrere Bestellungen über dieselbe Anführungszeichen-ID platziert werden können. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 installiert ist. Die Patch-ID ist ACSD-51819. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Es können mehrere Bestellungen mit derselben Angebots-ID platziert werden.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich als Benutzer an.
1. Fügen Sie Artikel zum Warenkorb hinzu und fahren Sie mit dem Checkout fort.
1. Wählen Sie eine Zahlungsmethode aus, klicken Sie aber nicht auf die **[!UICONTROL Place Order]** Schaltfläche.
1. Melden Sie sich bei demselben Konto in einem anderen Browser an.
1. Fahren Sie mit denselben Elementen fort, ohne auf die **[!UICONTROL Place Order]** Schaltfläche.
1. Klicken Sie auf **[!UICONTROL Place Order]** -Taste in beiden Systemen gleichzeitig angezeigt.
1. Validieren Sie die Bestellungen in beiden Browsern.

<u>Erwartete Ergebnisse</u>:

Nur die erste von einem Browser aufgegebene Bestellung wurde erfolgreich verarbeitet.

<u>Tatsächliche Ergebnisse</u>:

Bestellungen wurden in beiden Browsern platziert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
