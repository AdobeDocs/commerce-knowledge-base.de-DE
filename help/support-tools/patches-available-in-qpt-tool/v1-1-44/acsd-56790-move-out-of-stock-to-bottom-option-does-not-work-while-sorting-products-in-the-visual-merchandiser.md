---
title: '"ACSD-56790: **[!UICONTROL move out of stock to bottom]** kann beim Sortieren von Produkten in der  [!DNL Visual Merchandiser]'''
description: Wenden Sie den Patch ACSD-56790 an, um das Adobe Commerce-Problem zu beheben, bei dem die Option "Von Lager zu Ende wechseln"beim Sortieren von Produkten im Visual Merchandiser nicht funktioniert.
feature: Products, Categories
role: Admin, Developer
exl-id: a0c61696-a12d-4c1a-a061-e2f17f38e1f4
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# ACSD-56790: **[!UICONTROL move out of stock to bottom]** -Option funktioniert beim Sortieren von Produkten in der [!DNL Visual Merchandiser]

Der Patch ACSD-56790 behebt das Problem, dass die Option &quot;Von Lager zu Ende wechseln&quot;beim Sortieren von Produkten im [!DNL Visual Merchandiser]. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 ist installiert. Die Patch-ID ist ACSD-56790. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die **[!UICONTROL move out of stock to bottom]** -Option funktioniert beim Sortieren von Produkten in der [!DNL Visual Merchandiser]

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Adobe Commerce.
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** und erstellen Sie die folgenden Attribute.
1. Erstellen Sie eine neue Website: **Nicht-main**.
1. Erstellen Sie eine **Nicht-Hauptspeicher** auf dieser neuen Website.
1. Erstellen Sie zwei Stores:

   * Erste in der **Haupt-Website-Store**.
   * Die zweite in **Nicht-Hauptspeicher**.

1. Erstellen Sie zwei Quellen:
   * Briefe
   * Zahlen.

1. Erstellen Sie zwei Lager:
   * First Main - Vertriebskanäle: Haupt-Website - zugewiesene Quellen: Briefe.
   * Zweite Nicht-Haupt- Absatzkanäle: Nicht-Haupt - zugewiesene Quellen: Zahlen.

1. Erstellen Sie auf beiden Websites drei einfache Produkte, alle in der Kategorie Standard , die beiden Quellen zugeordnet sind:

   * ProductA - Qty *10* in Briefen, Menge *0* in Zahlen.
   * Product1 - Qty *0* in Briefen, Menge *10* in Zahlen.
   * ProductA1 - Qty *10* in Briefen, Menge *10* in Zahlen.

1. Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** und wählen  **[!UICONTROL Default category]**.
1. Ändern Sie den Umfang in **Erste**.
1. Erweitern Sie die Produkte im Abschnitt Kategorie .
1. Wählen Sie die Sortierreihenfolge aus: **[!UICONTROL move out of stock to bottom]**

<u>Erwartete Ergebnisse</u>:

Das Verzeichnis der Erzeugnisse mit der **nicht vorrätig** Produkte werden nach unten verschoben.

<u>Tatsächliche Ergebnisse</u>:

Die Produkte werden nicht geladen. Eine Seite leitet mit der Fehlermeldung zum Admin-Dashboard weiter: `Invalid security or form key. Please refresh the page`

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
