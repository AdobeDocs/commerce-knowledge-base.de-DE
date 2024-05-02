---
title: "ACSD-51358: Zeitplanaktualisierungen fehlen"
description: Wenden Sie den Patch ACSD-51358 an, um das Adobe Commerce-Problem zu beheben, bei dem Änderungen bei der geplanten Aktualisierung ohne Enddatum dazu führen, dass andere geplante Aktualisierungen für dieselbe Entität entfernt werden.
feature: Staging
role: Admin, Developer
exl-id: 8bc4c505-9cf2-4c33-93a1-4b4d7d0dfc15
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51358: Zeitplanaktualisierungen fehlen

Der Patch ACSD-51358 behebt das Problem, dass Änderungen bei geplanten Aktualisierungen ohne Enddatum dazu führen, dass andere geplante Aktualisierungen für dieselbe Entität entfernt werden. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 installiert ist. Die Patch-ID ist ACSD-51358. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Änderungen bei der geplanten Aktualisierung ohne Enddatum führen dazu, dass andere geplante Aktualisierungen für dieselbe Entität entfernt werden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine **[!UICONTROL scheduled update]** ohne Enddatum (*Update 1*).
1. Neu erstellen **[!UICONTROL scheduled update]** mit demselben Startdatum wie das erste Update, jedoch mit dem nächsten Tag und dem Enddatum (*Update 2*).
1. Bearbeiten **[!UICONTROL scheduled update]** erstellt in Schritt 1 (*Update 1*) und die Änderungen speichern.

<u>Erwartete Ergebnisse</u>

Die (*Update 2*) sollte im **[!UICONTROL schedule update]** list when (*Update 1*) bearbeitet wird.

<u>Tatsächliche Ergebnisse</u>

Die (*Update 2*) wurde aus der **[!UICONTROL schedule update]** list when (*Update 1*) bearbeitet wird.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] Handbuch.
