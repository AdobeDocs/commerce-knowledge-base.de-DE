---
title: "ACSD-51294: Preis, Menge, Steuern, Versand, Umsatz als Zeichenfolge an [!DNL Google Analytics] und GTM gesendet"
description: Wenden Sie den Patch ACSD-51294 an, um das Adobe Commerce-Problem zu beheben, bei dem Preis, Menge, Steuer, Versand und Umsatz als Zeichenfolge an [!DNL Google Analytics] und GTM gesendet werden.
feature: Orders, Shipping/Delivery, Variables
role: Admin
exl-id: 159e1e98-0def-4b20-901d-f5f58c3ead7c
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51294: Preis, Menge, Steuern, Versand, Umsatz als Zeichenfolge an [!DNL Google Analytics] und GTM gesendet

Der Patch ACSD-51294 behebt das Problem, dass Preis, Menge, Steuer, Versand und Umsatz als Zeichenfolge an [!DNL Google Analytics] und GTM gesendet werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.32 installiert ist. Die Patch-ID ist ACSD-51294. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Preis, Menge, Steuer, Versand und Umsatz werden als Zeichenfolge an [!DNL Google Analytics] und GTM gesendet.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie [!DNL Google Tag Manager], indem Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]** > **[!UICONTROL Google GTag]** > **[!UICONTROL Google Analytics4]** navigieren.
2. Erstellen Sie ein einfaches Produkt.
3. Führen Sie den Checkout mit diesem Produkt durch.
4. Überprüfen Sie die Variable &quot;`dataLayer` JavaScript&quot;auf der Erfolgsseite des Checkout.

<u>Erwartete Ergebnisse</u>

Preis- und Mengenwerte sind numerisch.

<u>Tatsächliche Ergebnisse</u>

Preis- und Mengenwerte sind Zeichenfolgen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] -Handbuch.
