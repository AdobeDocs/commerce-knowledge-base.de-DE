---
title: "ACSD-48212: Beim Produktimport wird das Produkt der falschen Quelle zugewiesen."
description: Wenden Sie den Patch ACSD-48212 an, um das Adobe Commerce-Problem zu beheben, bei dem der Produktimport das Produkt der falschen Quelle zuordnet.
exl-id: b3426f62-f73a-4b76-8e0e-544a9133720f
feature: Admin Workspace, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-48212: Beim Produktimport wird das Produkt der falschen Quelle zugewiesen.

Der Patch ACSD-48212 behebt das Problem, dass der Produktimport das Produkt der falschen Quelle zuordnet. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 installiert ist. Die Patch-ID lautet ACSD-48212. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Produktimport weist das Produkt der falschen Quelle zu.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine sekundäre Inventarquelle.
1. Erstellen Sie ein Produkt nur mit der standardmäßigen Inventarquelle.
1. Exportieren Sie das Produkt.
1. Ausführen `bin/magento cron:run`.
1. Öffnen **[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]**.
1. Wählen Sie das Produkt aus dem Raster aus.
1. Aufheben der Zuweisung des Lagers mithilfe der *[!UICONTROL mass action]* Menü.
1. Ausführen `bin/magento cron:run`.
1. Zuweisen der sekundären Quelle mithilfe der *[!UICONTROL mass action]* Menü.
1. Ausführen `bin/magento cron:run`.
1. Löschen Sie das Produkt mithilfe der *[!UICONTROL mass action]* Menü.
1. Ausführen `bin/magento cron:run`.
1. Importieren Sie das Produkt mit der zuvor exportierten CSV-Datei.
1. Überprüfen Sie die Quellzuweisung.

<u>Erwartete Ergebnisse</u>:

Das Produkt wird nur der Standardquelle zugewiesen.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt wird sowohl der Standard- als auch der sekundären Quelle zugewiesen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
