---
title: 'MDVA-42950: Videos werden nicht auf der Produktseite wiedergegeben'
description: Der Patch MDVA-42950 behebt das Problem, dass Videos nicht auf der Produktseite wiedergegeben werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42950. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: e19e5ff0-9ddd-41de-b64b-4c3aef4d16a5
feature: Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# MDVA-42950: Videos werden nicht auf der Produktseite wiedergegeben

Der Patch MDVA-42950 behebt das Problem, dass Videos nicht auf der Produktseite wiedergegeben werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42950. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Videos werden nicht auf der Produktseite wiedergegeben.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie den YouTube-API-Schlüssel, indem Sie zu &quot;**Stores**&quot;> &quot;**Konfiguration**&quot;> &quot;**Katalog**&quot;> &quot;**Produktvideo**&quot;navigieren.
1. Fügen Sie ein Video aus YouTube zu einem einfachen Produkt hinzu, das über eine konfigurierbare übergeordnete Komponente verfügt.
1. Fügen Sie die KOPFZEILE-HTML in Inhalt > **Design** > **Konfiguration** > **HTML-Head** > **Skripte und Stylesheets** hinzu:

   ```HTML
   <script async="" src="https://www.youtube.com/iframe_api"></script>`
   ```

1. Wechseln Sie zur Produktdetailseite und wählen Sie die Produktkonfiguration aus, um das Video in der Liste der Fotos und Videos anzuzeigen.
1. Versuchen Sie, das Video abzuspielen.

<u>Erwartete Ergebnisse</u>:

Video wird wiedergegeben.

<u>Tatsächliche Ergebnisse</u>:

Video wird nicht wiedergegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbar sind, in unserer Entwicklerdokumentation.
