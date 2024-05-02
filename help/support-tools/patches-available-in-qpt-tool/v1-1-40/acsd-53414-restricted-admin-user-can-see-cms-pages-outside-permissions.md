---
title: "ACSD-53414: Eingeschränkte Administratoren können CMS-Seiten außerhalb ihres Berechtigungsbereichs anzeigen."
description: Wenden Sie den Patch ACSD-53414 an, um das Adobe Commerce-Problem zu beheben, bei dem ein eingeschränkter Administrator CMS-Seiten außerhalb des Berechtigungsbereichs anzeigen kann.
feature: CMS
role: Admin, Developer
exl-id: f8540d52-a3bb-49bb-8868-7b1db03e571b
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-53414: Eingeschränkte Administratoren können CMS-Seiten außerhalb ihres Berechtigungsbereichs anzeigen

Der Patch ACSD-53414 behebt das Problem, dass ein eingeschränkter Administrator CMS-Seiten außerhalb des Berechtigungsbereichs anzeigen kann. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 ist installiert. Die Patch-ID ist ACSD-53414. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eingeschränkte Admin-Benutzer können CMS-Seiten über ihren Berechtigungsbereich hinaus sehen.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue Website (sub_website), speichern Sie (sub_store) und speichern Sie die Vorschau (sub_storeview).
1. Erstellen Sie eine Rolle &quot;sub_experte&quot;, die den Umfang von sub_website und sub_store zulässt. Weisen Sie nur die folgenden Berechtigungen zu: [!UICONTROL Dashboard] und [!UICONTROL Pages].
1. Erstellen Sie einen neuen Admin-Benutzer und weisen Sie ihn der Rolle sub_experte zu.
1. Weisen Sie die folgenden CSM-Seiten zu &quot;sub_storeview&quot;und &quot;default storeview&quot;zu.

   * [!UICONTROL 404 Not Found] > Zwischenspeicher
   * [!UICONTROL 503 Service Unavailable] > Standardspeicher

1. Melden Sie sich mit dem in Schritt 3 erstellten Admin-Benutzer bei Admin an.
1. Überprüfen Sie das Raster der CMS-Seiten.

<u>Erwartete Ergebnisse</u>:

*[!UICONTROL 503 Service Unavailable]* -Seite für den Webadministrator nicht sichtbar ist.

<u>Tatsächliche Ergebnisse</u>:

*[!UICONTROL 503 Service Unavailable]* ist für den Webadministrator sichtbar.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
