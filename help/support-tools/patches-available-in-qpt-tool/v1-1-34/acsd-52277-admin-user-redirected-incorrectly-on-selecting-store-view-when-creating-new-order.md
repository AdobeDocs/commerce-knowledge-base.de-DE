---
title: 'ACSD-52277: Admin-Benutzer hat beim Auswählen der Store-Ansicht beim Erstellen einer neuen Bestellung fälschlicherweise umgeleitet.'
description: Wenden Sie den Patch ACSD-52277 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Admin-Benutzer nach Auswahl der Store-Ansicht beim Erstellen einer neuen Bestellung in Admin nicht ordnungsgemäß umgeleitet wird.
exl-id: 6f0b86ae-f6f1-44cf-aef5-64def5f14824
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-52277: Admin-Benutzer hat beim Erstellen einer neuen Bestellung fälschlicherweise die Auswahl der Store-Ansicht umgeleitet

Der Patch ACSD-52277 behebt das Problem, dass ein Admin-Benutzer nach Auswahl der Store-Ansicht beim Erstellen einer neuen Bestellung in Admin nicht ordnungsgemäß umgeleitet wird. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 ist installiert. Die Patch-ID ist ACSD-52277. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4, 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein Admin-Benutzer wird nicht ordnungsgemäß umgeleitet, nachdem beim Erstellen einer neuen Bestellung die Store-Ansicht ausgewählt wurde.

<u>Zu reproduzierende Schritte</u>

1. Installieren Sie eine saubere Instanz.
1. Erstellen Sie ein Produkt.
1. Erstellen Sie eine zusätzliche Website, einen Store und zwei Store-Ansichten.
1. Erstellen Sie eine Bestellung über Admin durch Auswahl von *Store-Ansicht 1*.

<u>Erwartete Ergebnisse</u>:

Der Benutzer wird zur Bestellseite weitergeleitet.

<u>Tatsächliche Ergebnisse</u>:

Der Benutzer wird nach Auswahl der Store-Ansicht nicht zur Bestellseite weitergeleitet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
