---
title: "ACSD-56090: GraphQL-Antwort ist nicht speicherspezifisch"
description: Wenden Sie den Patch ACSD-56090 an, um das Adobe Commerce-Problem zu beheben, bei dem die GraphQL-Antwort alle Speicherdaten anstelle der Store-spezifischen Daten enthält.
feature: GraphQL
role: Admin, Developer
exl-id: 129491e0-1a77-4ccc-8aba-cd0afdb26176
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-56090: GraphQL-Antwort ist nicht speicherspezifisch

Der Patch ACSD-56090 behebt das Problem, dass die GraphQL-Antwort alle Speicherdaten anstelle der Store-spezifischen Daten enthält. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 ist installiert. Die Patch-ID ist ACSD-56090. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die GraphQL-Antwort enthält alle Speicherdaten anstelle der Store-spezifischen Daten.

<u>Zu reproduzierende Schritte</u>:

1. Anmelden bei **[!UICONTROL Admin panel]** > **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** und erstellen Sie zwei Stammkategorien.
1. Jede Stammkategorie sollte eine Unterkategorie aufweisen.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL All stores]** > Zwei Stores existieren mit unterschiedlichen Stammkategorien für jeden von ihnen. (Jeder Speicher sollte mindestens eine Store-Ansicht haben.)
1. Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > ein Produkt erstellen mit

* Alle zugewiesenen Stamm- und Unterkategorien
* Alle zugewiesenen Websites.

1. Führen Sie die GraphqQL-Abfrage aus (add header — store = &#39;storename ):

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

1. Überprüfen Sie die Antwort nach der Ausführung der GraphqQL-Abfrage.

<u>Erwartete Ergebnisse</u>:

Die Store-spezifischen Daten werden zurückgegeben

<u>Tatsächliche Ergebnisse</u>:

Die zurückgegebenen Daten sind nicht speicherspezifisch.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
