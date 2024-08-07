---
title: "ACSD-51379: Änderungen am Textinhalt der Seite über [!DNL Page Builder] werden nicht gespeichert."
description: Wenden Sie den Patch ACSD-51379 an, um das Adobe Commerce-Problem zu beheben, bei dem die über [!DNL Page Builder] vorgenommenen Änderungen am Textinhalt einer Seite nicht gespeichert werden.
exl-id: e274ca03-b675-4ded-9820-1d60978685d0
feature: Page Builder, Page Content
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# ACSD-51379: Änderungen am Textinhalt der Seite über [!DNL Page Builder] werden nicht gespeichert

Der Patch ACSD-51379 behebt das Problem, dass Änderungen, die über [!DNL Page Builder] am Textinhalt einer Seite vorgenommen wurden, nicht gespeichert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 installiert ist. Die Patch-ID ist ACSD-51379. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Änderungen, die über [!DNL Page Builder] am Textinhalt einer Seite vorgenommen wurden, werden nicht gespeichert.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Admin an.
1. Gehen Sie zu **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**.
1. Erstellen Sie auf der Registerkarte **[!UICONTROL Content]** eine Testseite mit einer Zeile und einem Textelement.
1. Speichern Sie die Seite und kehren Sie zur Registerkarte **[!UICONTROL Content]** zurück.
1. Bearbeiten Sie den Text, indem Sie ihn auswählen und ändern.

   **Hinweis:** Das Problem kann nur reproduziert werden, wenn der Text ausgewählt und geändert wird, ohne den Editor zu aktivieren.

1. Klicken Sie auf der Testseite auf die Schaltfläche **[!UICONTROL Save and Close]** .
1. Öffnen Sie die Testseite erneut und überprüfen Sie die Registerkarte **[!UICONTROL Content]** .

<u>Erwartete Ergebnisse</u>:

Der neue Text wird erfolgreich für ursprüngliche und duplizierte Textelemente gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Das Textelement wurde erfolgreich dupliziert, der neue Text wird jedoch nicht gespeichert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
