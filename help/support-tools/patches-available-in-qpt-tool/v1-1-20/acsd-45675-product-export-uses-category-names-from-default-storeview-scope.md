---
title: "ACSD-45675: Beim Export von Produkten werden Kategorienamen aus dem standardmäßigen Speicheransichtsbereich verwendet."
description: Der Patch ACSD-45675 behebt das Problem, dass beim Export von Produkten Kategorienamen aus dem standardmäßigen Store-Ansichtsbereich verwendet werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 installiert ist. Die Patch-ID ist ACSD-45675. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
exl-id: 9edd718e-4c0c-44dd-b802-07c9ec7c182a
feature: Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-45675: Beim Export von Produkten werden Kategorienamen aus dem standardmäßigen Speicheransichtsbereich verwendet

Der Patch ACSD-45675 behebt das Problem, dass beim Export von Produkten Kategorienamen aus dem standardmäßigen Store-Ansichtsbereich verwendet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 installiert ist. Die Patch-ID ist ACSD-45675. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Export von Produkten werden Kategorienamen aus dem standardmäßigen Umfang der Store-Ansicht verwendet.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine benutzerdefinierte Store-Ansicht **[!UICONTROL Thai]** im Hauptspeicher.
1. Machen Sie **[!UICONTROL Thai]** zur standardmäßigen Store-Ansicht der Haupt-Website.
1. Erstellen Sie die folgende Kategoriestruktur unter **[!UICONTROL Default Category]**:

   *[!UICONTROL Default category/Tea/Black]*

1. Wählen Sie die Kategorie **[!UICONTROL Tea]** aus und ändern Sie die **[!UICONTROL Scope]** in **[!UICONTROL Thai]**.
1. Setzen Sie die **[!UICONTROL Category Name]** auf **[!UICONTROL ชาดำ]**.
1. Erstellen Sie ein einfaches Produkt **[!UICONTROL SP001]** und weisen Sie die Kategorie **[!UICONTROL Black]** zu.
1. Vergewissern Sie sich, dass der Cron nicht ausgeführt wird.
1. Führen Sie einen Produktexport durch. Nach SKU filtern und **[!UICONTROL SP001]** auswählen.
1. Überprüfen Sie die Spalte **[!UICONTROL categories]** im exportierten CSV.

<u>Erwartete Ergebnisse</u>:

Da beim Export kein Store ausgewählt wurde, sollte ein Kategoriepfad wie der folgende abgerufen werden: *[!UICONTROL Default Category/Tea/Black]*.

<u>Tatsächliche Ergebnisse</u>:

Der Kategoriepfad weist verschiedene Sprachen auf: *[!UICONTROL Default Category/ชาดำ/Black]*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tools] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im Handbuch zum Werkzeug für Qualitätsmuster.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in [!DNL QPT] verfügbaren Patches finden Sie unter [In  [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbare Patches im Handbuch zum Werkzeug für Qualitätsmuster .
