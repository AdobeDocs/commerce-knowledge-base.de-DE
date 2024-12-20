---
title: 'ACSD-58442: Behebung des Problems, bei dem Geräte mit 768 px Breite als Mobilgeräte behandelt wurden, wodurch Menü und Kopfzeile in der Mobile-Ansicht und nicht auf dem Desktop geladen wurden'
description: Wenden Sie den Patch ACSD-58442 an, um das Adobe Commerce-Problem zu beheben, bei dem Geräte mit einer Breite von 768 px als Mobilgeräte behandelt werden, wodurch das Menü und die Kopfzeile in einer mobilen Ansicht statt auf dem Desktop geladen werden.
feature: Storefront
role: Admin, Developer
exl-id: 05d812b9-c5f5-4397-9755-bed2424e70b3
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-58442: Behebung des Problems, bei dem Geräte mit 768 px Breite als Mobilgeräte behandelt wurden, wodurch Menü und Kopfzeile in der Mobile-Ansicht und nicht auf dem Desktop geladen wurden

Der Patch ACSD-58442 behebt das Adobe Commerce-Problem, bei dem Geräte mit einer Breite von 768 px als Mobilgeräte behandelt werden, wodurch das Menü und die Kopfzeile in einer mobilen Ansicht statt auf einem Desktop geladen werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 installiert ist. Die Patch-ID ist ACSD-58442. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das System behandelt Geräte mit einer Breite von 768 px jetzt als Desktop, um sicherzustellen, dass Menü und Kopfzeile korrekt geladen werden. Zuvor wurden Geräte mit einer Breite von 768 px als Mobilgeräte behandelt, wodurch das Menü und die Kopfzeile in einer Mobile-Ansicht geladen wurden.

<u>Zu reproduzierende Schritte</u>:

1. Laden Sie die Startseite auf eine iPad Mini oder verwenden Sie das Überprüfungstool eines Browsers, um die Größe des Browsers auf eine Breite von *768px* zu ändern.
1. Öffnen Sie das Hauptmenü.

<u>Erwartete Ergebnisse</u>:

Menü und Kopfzeile werden als Desktop-Ansicht geladen.

<u>Tatsächliche Ergebnisse</u>:

Menü und Kopfzeile werden als Mobile-Ansicht geladen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
