---
title: '"ACSD-47137: Bildgalerie-Ladegeschwindigkeit verbessern "pub/media" Ordner "big"'
description: Wenden Sie den Patch ACSD-47137 an, um die Ladegeschwindigkeit der Bildergalerie zu verbessern, wenn der Ordner "pub/media"sehr groß ist.
exl-id: 43268909-6845-4d1d-b6b8-4ae0ce40fd5e
feature: Cache, Catalog Management, Categories, Media
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-47137: Verbesserung der Ladegeschwindigkeit von Bildergalerien bei `pub/media` Ordner groß

Der Patch ACSD-47137 verbessert die Ladegeschwindigkeit der Bildergalerie, wenn die `pub/media` Ordner ist sehr groß. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 ist installiert. Die Patch-ID ist ACSD-47137. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Ladegeschwindigkeit der Bildgalerie ist langsam, wenn die `pub/media` Ordner ist sehr groß.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu Adobe Commerce Admin > **[!UICONTROL STORES]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** > **[!UICONTROL Enable Old Media Gallery]** nach _Nein_.
1. Bereinigen Sie den Konfigurationscache.
1. Melden Sie sich ab und melden Sie sich erneut als Administrator an.
1. Navigieren Sie in der Admin-Seitenleiste zu **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** und wählen Sie die Stammkategorie aus.
1. Erweitern Sie die **[!UICONTROL Content]** und klicken Sie auf **[!UICONTROL Select from Gallery]**.

Beim Laden der Seite sendet Adobe Commerce `media_gallery/directories/gettree` Anfrage zum Laden der Ordnerstruktur für Medien.

<u>Erwartete Ergebnisse</u>:

Die `media_gallery/directories/gettree` -Anfrage sollte Inhalt nur aus den erforderlichen Ordnern laden, außer dass die gesamte Pfadliste aus der Schleife `pub/media/` Ordner.

<u>Tatsächliche Ergebnisse</u>:

Die `media_gallery/directories/gettree` Das Laden einer Anforderung dauert lange, wenn die Variable `pub/media/` -Ordner enthält viele Inhalte.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
