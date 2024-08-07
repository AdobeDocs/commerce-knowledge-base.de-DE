---
title: "ACSD-55427: Ein Administrator kann die Zuweisung eines Produkts von **[!UICONTROL Product in Shared Catalogs]** auf der Produktseite nicht aufheben."
description: Wenden Sie den Patch ACSD-55427 an, um das Adobe Commerce-Problem zu beheben, bei dem die Zuweisung eines Produkts nicht von **[!UICONTROL Product in Shared Catalogs]** aufgehoben werden kann.
feature: Products, B2B
role: Admin, Developer
exl-id: 1e08def1-07f6-42e0-b600-9f0bfdd6477a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-55427: Ein Administrator kann die Zuweisung eines Produkts von **[!UICONTROL Product in Shared Catalogs]** auf der Produktseite nicht aufheben.

Der Patch ACSD-55427 behebt das Problem, dass Sie die Zuweisung eines Produkts von &quot;**[!UICONTROL Product in Shared Catalogs]**&quot;auf der Produktseite im Katalog in der Commerce-Admin nicht aufheben können. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 installiert ist. Die Patch-ID ist ACSD-55427. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Sie können die Zuweisung eines Produkts von &quot;**[!UICONTROL Product in Shared Catalogs]**&quot;auf der Produktseite im Katalog in der Commerce-Admin-Konsole nicht aufheben.

<u>Zu reproduzierende Schritte</u>:

Voraussetzungen: Adobe Commerce wird mit aktiviertem B2B und **[!UICONTROL Shared Catalogs]** installiert.
1. Erstellen Sie ein Produkt.
1. Navigieren Sie zum Dashboard des freigegebenen Katalogs und öffnen Sie den standardmäßigen freigegebenen Katalog.
1. Zuweisen des Produkts zum Standardkatalog und Festlegen eines Preises, der unter dem Produktpreis liegt.
1. Speichern Sie den freigegebenen Katalog.
1. Führen Sie die [!UICONTROL CRON] aus, um die Verbraucher/Indexer zu aktualisieren.
1. Öffnen Sie das Produkt und entfernen Sie es unter dem Abschnitt &quot;**[!UICONTROL Product in Shared Catalogs]**&quot;.

<u>Erwartete Ergebnisse</u>:

Das Produkt sollte unter dem Abschnitt **[!UICONTROL Product in Shared Catalogs]** entfernt werden.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt wird weiterhin im Abschnitt **[!UICONTROL Product in Shared Catalogs]** angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
