---
title: "ACSD-50895: [!DNL Google Analytics] 3 GTM-Tags werden nicht ausgelöst, wenn [!DNL Google Analytics] 4 GTM ist nicht konfiguriert."
description: Wenden Sie den Patch ACSD-50895 an, um das Adobe Commerce-Problem zu beheben, bei dem [!DNL Google Analytics] 3 GTM-Tags werden nicht ausgelöst, wenn [!DNL Google Analytics] 4 GTM ist nicht konfiguriert.
role: Admin
exl-id: da48f6f1-a68b-4a9c-a79a-d7bd01b65dc2
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-50895: [!DNL Google Analytics] 3 GTM-Tags werden nicht ausgelöst, wenn [!DNL Google Analytics] 4 GTM ist nicht konfiguriert

Der Patch ACSD-50895 behebt das Problem, bei dem [!DNL Google Analytics] 3 GTM-Tags werden nicht ausgelöst, wenn [!DNL Google Analytics] 4 GTM ist nicht konfiguriert. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 installiert ist. Die Patch-ID ist ACSD-50895. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

[!DNL Google Analytics] 3 GTM-Tags werden nicht ausgelöst, wenn [!DNL Google Analytics] 4 GTM ist nicht konfiguriert.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich als Administrator an.
1. Aktivieren **[!DNL Google Analytics 3]** und **[!DNL Google Tag Manager]** in **Admin** > **Store** > **Konfiguration** > **Vertrieb** > **Google-API** > **Google Analytics**.
1. Aktivieren Sie nicht die **[!DNL Google Analytics 4]** und **[!DNL Google Tag Manager]**.
1. Öffnen Sie die Produktseite in der Storefront.

<u>Erwartete Ergebnisse</u>:

Die GTM-Tags werden nur ausgelöst, wenn **[!DNL Google Analytics]** 3 GTM ist aktiviert.

<u>Tatsächliche Ergebnisse</u>:

Die GTM-Tags werden bei **[!DNL Google Analytics]** 4 GTM ist deaktiviert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
