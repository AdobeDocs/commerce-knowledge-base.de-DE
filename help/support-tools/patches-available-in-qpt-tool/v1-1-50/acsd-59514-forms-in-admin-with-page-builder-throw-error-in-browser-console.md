---
title: 'ACSD-59514: Forms in Admin mit dem Fehler [!DNL Page Builder] Throw error in der Browser-Konsole'
description: Wenden Sie den Patch ACSD-59514 an, um das Adobe Commerce-Problem zu beheben, bei dem Formulare in Admin mit  [!DNL Page Builder] den Fehler "[!DNL Page Builder] wurde 5 Sekunden lang gerendert, ohne Sperren freizugeben". in der Browser-Konsole nach dem Senden des Formulars, und die Änderungen können nicht gespeichert werden.
feature: Page Builder
role: Admin, Developer
source-git-commit: 19ecaa6b287d63bfae00c51911b53e1ed7ab5ed8
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---


# ACSD-59514: Forms in Admin mit [!DNL Page Builder] Fehler in der Browserkonsole auslösen

Der Patch ACSD-59514 behebt das Problem, dass die Formulare in Admin mit [!DNL Page Builder] den Fehler *[!DNL Page Builder]5 Sekunden lang wiedergegeben haben, ohne Sperren zu veröffentlichen.* in der Browser-Konsole nach dem Senden des Formulars und Änderungen können nicht gespeichert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 installiert ist. Die Patch-ID ist ACSD-59514. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Forms in Admin mit [!DNL Page Builder] gibt den Fehler aus, dass *[!DNL Page Builder]5 Sekunden lang gerendert wurde, ohne Sperren zu veröffentlichen.* in der Browser-Konsole nach dem Senden des Formulars und Änderungen können nicht gespeichert werden.

<u>Voraussetzungen</u>:

Adobe Commerce [!DNL Page Builder] -Module werden installiert und aktiviert.

<u>Zu reproduzierende Schritte</u>:

1. Öffnen Sie das Admin-Bedienfeld und klicken Sie auf die Schaltfläche [!UICONTROL Content] .
1. Markieren Sie den Baustein und öffnen Sie ihn.
1. Ändern Sie den Inhalt und klicken Sie auf [!UICONTROL Save].
1. Öffnen Sie die Konsole und sehen Sie die Fehlermeldung.

<u>Erwartete Ergebnisse</u>:

Der Block wurde erfolgreich gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Der Lader dreht sich nicht mehr, und der Block wird nicht gespeichert. Der folgende Fehler wird in der Browser-Konsole angezeigt:
*[!DNL Page Builder]wurde 5 Sekunden lang gerendert, ohne Sperren freizugeben.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
