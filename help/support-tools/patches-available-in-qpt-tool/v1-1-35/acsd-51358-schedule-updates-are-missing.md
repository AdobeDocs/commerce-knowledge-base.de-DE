---
title: 'ACSD-51358: Zeitplanaktualisierungen fehlen'
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

Der Patch ACSD-51358 behebt das Problem, dass Änderungen bei geplanten Aktualisierungen ohne Enddatum dazu führen, dass andere geplante Aktualisierungen für dieselbe Entität entfernt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 installiert ist. Die Patch-ID ist ACSD-51358. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Änderungen bei der geplanten Aktualisierung ohne Enddatum führen dazu, dass andere geplante Aktualisierungen für dieselbe Entität entfernt werden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen **[!UICONTROL scheduled update]** -Wert ohne Enddatum (*update 1*).
1. Erstellen Sie einen neuen **[!UICONTROL scheduled update]** -Wert mit demselben Startdatum wie das erste Update, fügen Sie jedoch den nächsten Tag und das Enddatum hinzu (*update 2*).
1. Bearbeiten Sie **[!UICONTROL scheduled update]** , der für Schritt 1 (*update 1*) erstellt wurde, und die Speicheränderungen.

<u>Erwartete Ergebnisse</u>

Das (*Update 2*) sollte in der Liste **[!UICONTROL schedule update]** verbleiben, wenn (*Update 1*) bearbeitet wird.

<u>Tatsächliche Ergebnisse</u>

(*update 2*) wurde aus der Liste **[!UICONTROL schedule update]** entfernt, wenn (*update 1*) bearbeitet wird.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] -Handbuch.
