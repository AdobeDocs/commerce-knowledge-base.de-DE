---
title: 'ACSD-47336: [!UICONTROL Something went wrong] Fehler beim Verwerfen von Benachrichtigungen in Adobe Commerce Admin'
description: Wenden Sie den Patch ACSD-47336 an, um das Adobe Commerce-Problem zu beheben, bei dem dem Benutzer beim Verwerfen von Benachrichtigungen in der  [!DNL Commerce] Admin-Instanz der Fehler [!UICONTROL Something went wrong] angezeigt wird.
exl-id: 7561f055-ce04-4a49-8c58-271c24420a60
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-47336: _[!UICONTROL Something went wrong]_Fehler beim Verwerfen von Benachrichtigungen in Adobe Commerce Admin

Der Patch ACSD-47336 behebt das Problem, bei dem der Benutzer den Fehler _[!UICONTROL Something went wrong]_beim Verwerfen von Benachrichtigungen in [!DNL Commerce] Admin sieht. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 installiert ist. Die Patch-ID ist ACSD-47336. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden): 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden): 2.4.0 - 2.4.5 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Benutzer sieht den Fehler _[!UICONTROL Something went wrong]_, wenn er Benachrichtigungen in [!DNL Commerce] Admin ablehnt.

<u>Zu reproduzierende Schritte</u>:

1. Führen Sie einen Massenvorgang durch (z. B. eine Massenaktualisierung von Produktattributen aus dem Produktraster).
1. Führen Sie den Vorgang aus (z. B. `bin/magento queue:consumer:start product_action_attribute.update`).
1. Aktualisieren Sie die Seite &quot;[!DNL Commerce] Admin&quot;, erweitern Sie den Abschnitt &quot;Admin-Benachrichtigung&quot;und klicken Sie auf den Link &quot;**[!UICONTROL Dismiss All Completed Tasks]**&quot;.

<u>Erwartete Ergebnisse</u>:

Der Fehler _[!UICONTROL Something went wrong]_sollte beim Löschen der abgeschlossenen Aufgaben nicht angezeigt werden.

<u>Tatsächliche Ergebnisse</u>:

Der Fehler _[!UICONTROL Something went wrong]_wird angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
