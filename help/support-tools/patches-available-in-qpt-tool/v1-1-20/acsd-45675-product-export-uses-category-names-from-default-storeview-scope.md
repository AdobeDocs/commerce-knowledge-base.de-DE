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

Der Patch ACSD-45675 behebt das Problem, dass beim Export von Produkten Kategorienamen aus dem standardmäßigen Store-Ansichtsbereich verwendet werden. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 installiert ist. Die Patch-ID ist ACSD-45675. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Export von Produkten werden Kategorienamen aus dem standardmäßigen Umfang der Store-Ansicht verwendet.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen einer benutzerdefinierten Store-Ansicht **[!UICONTROL Thai]** im Hauptspeicher.
1. Make **[!UICONTROL Thai]** die standardmäßige Store-Ansicht der Haupt-Website.
1. Erstellen Sie die folgende Kategoriestruktur unter **[!UICONTROL Default Category]**:

   *[!UICONTROL Default category/Tea/Black]*

1. Kategorie auswählen **[!UICONTROL Tea]** und ändern Sie **[!UICONTROL Scope]** nach **[!UICONTROL Thai]**.
1. Legen Sie die **[!UICONTROL Category Name]** as **[!UICONTROL ชาดำ]**.
1. Einfaches Produkt erstellen **[!UICONTROL SP001]** und die Kategorie zuweisen **[!UICONTROL Black]**.
1. Vergewissern Sie sich, dass der Cron nicht ausgeführt wird.
1. Führen Sie einen Produktexport durch. Nach SKU filtern und auswählen **[!UICONTROL SP001]**.
1. Überprüfen Sie die **[!UICONTROL categories]** in der exportierten CSV-Datei.

<u>Erwartete Ergebnisse</u>:

Da beim Export kein Speicher ausgewählt wurde, sollte ein Kategoriepfad wie der folgende angezeigt werden: *[!UICONTROL Default Category/Tea/Black]*.

<u>Tatsächliche Ergebnisse</u>:

Der Kategoriepfad hat unterschiedliche Sprachen: *[!UICONTROL Default Category/ชาดำ/Black]*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tools] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im Handbuch &quot;Qualitätsmuster-Tool&quot;.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) in unserer Wissensdatenbank.

Weitere Informationen zu anderen Patches finden Sie unter [!DNL QPT], siehe [In verfügbaren Patches [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im Handbuch &quot;Qualitätsmuster-Tool&quot;.
