---
title: "ACSD-51379: Änderungen am Textinhalt der Seite über [!DNL Page Builder] nicht gespeichert werden."
description: Wenden Sie den Patch ACSD-51379 an, um das Adobe Commerce-Problem zu beheben, bei dem die Änderungen am Textinhalt einer Seite über [!DNL Page Builder] nicht gespeichert werden.
exl-id: e274ca03-b675-4ded-9820-1d60978685d0
feature: Page Builder, Page Content
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# ACSD-51379: Änderungen am Textinhalt der Seite über [!DNL Page Builder] nicht gespeichert werden

Der Patch ACSD-51379 behebt das Problem, dass die Änderungen, die über an den Textinhalten einer Seite vorgenommen wurden [!DNL Page Builder] nicht gespeichert werden. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 installiert ist. Die Patch-ID ist ACSD-51379. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Änderungen, die über an den Textinhalten einer Seite vorgenommen wurden [!DNL Page Builder] nicht gespeichert werden.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Admin an.
1. Navigieren Sie zu **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**.
1. Erstellen Sie eine Testseite mit einer Zeile und einem Textelement im **[!UICONTROL Content]** Registerkarte.
1. Speichern Sie die Seite und kehren Sie zur **[!UICONTROL Content]** Registerkarte.
1. Bearbeiten Sie den Text, indem Sie ihn auswählen und ändern.

   **Hinweis:** Das Problem kann nur reproduzierbar sein, wenn der Text ausgewählt und geändert wurde, ohne den Editor zu aktivieren.

1. Klicken Sie auf **[!UICONTROL Save and Close]** auf der Testseite.
1. Öffnen Sie die Testseite erneut und überprüfen Sie die **[!UICONTROL Content]** Registerkarte.

<u>Erwartete Ergebnisse</u>:

Der neue Text wird erfolgreich für ursprüngliche und duplizierte Textelemente gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Das Textelement wurde erfolgreich dupliziert, der neue Text wird jedoch nicht gespeichert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
