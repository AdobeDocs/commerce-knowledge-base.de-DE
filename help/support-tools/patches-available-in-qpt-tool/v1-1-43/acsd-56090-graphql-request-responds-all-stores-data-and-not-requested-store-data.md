---
title: 'ACSD-56090: GraphQL-Antwort ist nicht speicherspezifisch'
description: Wenden Sie den Patch ACSD-56090 an, um das Adobe Commerce-Problem zu beheben, bei dem die GraphQL-Antwort alle Speicherdaten und nicht die speicherspezifischen Daten enthält.
feature: GraphQL
role: Admin, Developer
exl-id: 129491e0-1a77-4ccc-8aba-cd0afdb26176
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-56090: GraphQL-Antwort ist nicht speicherspezifisch

Mit dem Patch ACSD-56090 wird das Problem behoben, dass die GraphQL-Antwort alle Speicherdaten und nicht die speicherspezifischen Daten enthält. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 installiert ist. Die Patch-ID ist ACSD-56090. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die GraphQL-Antwort enthält alle Speicherdaten anstelle der speicherspezifischen Daten.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich bei **[!UICONTROL Admin panel]** > **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** an und erstellen Sie zwei Stammkategorien.
1. Jede Stammkategorie sollte über eine Unterkategorie verfügen.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL All stores]** > Zwei Stores existieren mit unterschiedlichen Stammkategorien für jede von ihnen. (Jeder Store sollte mindestens eine Store-Ansicht haben)
1. Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > Erstellen eines Produkts mit

* Alle zugewiesenen Stamm- und Unterkategorien
* Alle Websites zugewiesen.

1. Führen Sie die GraphQL-Abfrage aus (Kopfzeile hinzufügen — store = &#39;storeName&#39;):

```
   query {
     products(filter: { url_key: { eq: "abc" } }) {
       items {
         categories {
           name
           id
           url_path
           breadcrumbs {
             category_id
             category_name
             category_level
           }
         }
       }
     }
   }
```

1. Überprüfen Sie die Antwort nach dem Ausführen der GraphQL-Abfrage.

<u>Erwartete Ergebnisse</u>:

Die speicherspezifischen Daten werden zurückgegeben

<u>Tatsächliche Ergebnisse</u>:

Die zurückgegebenen Daten sind nicht speicherspezifisch.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
