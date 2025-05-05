---
title: 'ACSD-55427: Ein Administrator kann die Zuweisung von Produkt zu **[!UICONTROL Product in Shared Catalogs]** auf der Produktseite nicht aufheben'
description: Wenden Sie den ACSD-55427 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die Zuweisung eines Produkts zu **[!UICONTROL Product in Shared Catalogs]** nicht aufgehoben werden kann.
feature: Products, B2B
role: Admin, Developer
exl-id: 1e08def1-07f6-42e0-b600-9f0bfdd6477a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-55427: Ein Administrator kann die Zuweisung von **[!UICONTROL Product in Shared Catalogs]** auf der Produktseite nicht aufheben

Mit dem Patch ACSD-55427 wird das Problem behoben, dass Sie die Zuweisung eines Produkts zu **[!UICONTROL Product in Shared Catalogs]** auf der Produktseite im Katalog in Commerce Admin nicht aufheben können. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 installiert ist. Die Patch-ID ist ACSD-55427. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Zuweisung eines Produkts zu einem **[!UICONTROL Product in Shared Catalogs]** auf der Produktseite im Katalog im Commerce-Admin-Bereich kann nicht aufgehoben werden.

<u>Schritte zur Reproduktion</u>:

Voraussetzungen: Adobe Commerce muss mit aktiviertem B2B- und **[!UICONTROL Shared Catalogs]** installiert werden.
1. Erstellen Sie ein Produkt.
1. Navigieren Sie zum Dashboard des freigegebenen Katalogs und öffnen Sie den standardmäßigen freigegebenen Katalog.
1. Das Produkt dem Standardkatalog zuweisen und einen Preis festlegen, der unter dem Produktpreis liegt.
1. Speichern Sie den freigegebenen Katalog.
1. Führen Sie die [!UICONTROL CRON] aus, um die Verbraucher/Indexer zu aktualisieren.
1. Öffnen Sie das Produkt und entfernen Sie das Produkt aus **[!UICONTROL Product in Shared Catalogs]** Abschnitt.

<u>Erwartete Ergebnisse</u>:

Das Produkt ist aus dem Abschnitt **[!UICONTROL Product in Shared Catalogs]** zu entfernen.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt wird weiterhin im Abschnitt **[!UICONTROL Product in Shared Catalogs]** angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
