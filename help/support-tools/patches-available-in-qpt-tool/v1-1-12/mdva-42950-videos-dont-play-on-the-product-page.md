---
title: 'MDVA-42950: Videos werden auf der Produktseite nicht wiedergegeben'
description: Der Patch MDVA-42950 löst das Problem, dass Videos auf der Produktseite nicht wiedergegeben werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42950. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: e19e5ff0-9ddd-41de-b64b-4c3aef4d16a5
feature: Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# MDVA-42950: Videos werden auf der Produktseite nicht wiedergegeben

Der Patch MDVA-42950 löst das Problem, dass Videos auf der Produktseite nicht wiedergegeben werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42950. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Videos werden nicht auf der Produktseite wiedergegeben.

<u>Schritte zur Reproduktion</u>:

1. Konfigurieren Sie den YouTube-API-Schlüssel, indem Sie **Stores** > **Configuration** > **Catalog** > **Produktvideo**.
1. Fügen Sie ein Video aus YouTube in jedes einfache Produkt ein, für das das übergeordnete Element konfigurierbar ist.
1. HEADER-HTML in Inhalt hinzufügen > **Design** > **Configuration** > **HTML Head** > **Scripts und Stylesheets**:

   ```HTML
   <script async="" src="https://www.youtube.com/iframe_api"></script>`
   ```

1. Gehen Sie zur PDP und wählen Sie Produktkonfiguration , um das Video in der Liste der Fotos und Videos anzuzeigen.
1. Versuchen Sie, das Video abzuspielen.

<u>Erwartete Ergebnisse</u>:

Video wird wiedergegeben.

<u>Tatsächliche Ergebnisse</u>:

Video wird nicht wiedergegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in unserer Entwicklerdokumentation.
