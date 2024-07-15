---
title: "ACSD-47988: Beim Produktexport werden HTML-Tags aus der Produktbeschreibung des Seitenaufbaus entfernt."
description: Wenden Sie den Patch ACSD-47988 an, um das Adobe Commerce-Problem zu beheben, bei dem der Produktexport HTML-Tags aus der Produktbeschreibung des Seitenaufbaus schneidet.
exl-id: 96c45ca8-f526-4876-8f2c-39bce07f86eb
feature: Admin Workspace, Data Import/Export, Page Builder, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-47988: Beim Produktexport werden HTML-Tags aus der Produktbeschreibung des Seitenaufbaus entfernt

Der Patch ACSD-47988 behebt das Problem, bei dem der Produktexport HTML-Tags aus der Produktbeschreibung des Seitenaufbaus schneidet. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 installiert ist. Die Patch-ID lautet ACSD-47988. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Produktexport werden HTML-Tags aus der Produktbeschreibung des Seitenaufbaus entfernt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie Produkte mit etwas HTML in der Beschreibung. Verwenden Sie das HTML-Element des Seitenaufbaus, um HTML-Tags einzufügen.
1. Exportieren Sie die Produkte mithilfe der Import-/Exportfunktion von Adobe Commerce.
1. Importieren Sie die exportierte CSV.
1. Öffnen Sie das Produkt und überprüfen Sie die HTML-Elemente unter der Beschreibung.

<u>Erwartete Ergebnisse</u>:

HTML-Tags bleiben nach dem Import desselben Inhalts in der Produktbeschreibung.

<u>Tatsächliche Ergebnisse</u>:

HTML-Tags werden nach dem Import entfernt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
