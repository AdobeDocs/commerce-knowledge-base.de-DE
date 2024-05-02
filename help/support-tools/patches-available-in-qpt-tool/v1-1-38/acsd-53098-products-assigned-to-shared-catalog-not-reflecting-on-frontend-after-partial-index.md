---
title: "ACSD-53098: Produkte im freigegebenen Katalog spiegeln nicht das Frontend wider."
description: Wenden Sie den Patch ACSD-53098 an, um das Adobe Commerce-Problem zu beheben, bei dem Produkte, die einem freigegebenen Katalog zugewiesen sind, beim Ausführen eines partiellen Index nicht auf dem Frontend angezeigt werden.
feature: B2B, Catalog Management, Categories, Products
role: Admin, Developer
exl-id: 19c66a3a-04b2-48ee-aff3-ad2b592ff876
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-53098: Produkte im freigegebenen Katalog werden nicht auf dem Frontend angezeigt

Der Patch ACSD-53098 behebt das Problem, dass Produkte, die einem freigegebenen Katalog zugeordnet sind, beim Ausführen eines partiellen Index nicht auf der Vorderseite erscheinen. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.38 installiert ist. Die Patch-ID ist ACSD-53098. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Produkte, die über API einem freigegebenen Katalog zugewiesen wurden, werden nicht an der Frontend angezeigt, nachdem der partielle Indexer den Cron-Auftrag ausgeführt hat, gefolgt von dem Consumer-Cron.

<u>Zu reproduzierende Schritte</u>:

1. Einrichten [!DNL RabbitMQ] als Warteschlangendienst.
1. Indexer zu wechseln **[!UICONTROL Update on Schedule]** -Modus.
1. Erstellen Sie einen freigegebenen Katalog und weisen Sie ihn einem Unternehmen zu.
1. Erstellen Sie ein einfaches Produkt und weisen Sie es einer Kategorie zu. Führen Sie die partielle Neuindizierung aus:

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. Verwenden Sie die folgende API-Anfrage, um das erstellte Produkt dem freigegebenen Katalog zuzuweisen.

   ```
   pub/rest/all/V1/sharedCatalog/<id>/assignProducts
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. Führen Sie den folgenden Cron aus, um die Warteschlangen zu leeren und die partielle Neuindizierung auszuführen:

   `bin/magento cron:run --group=consumers`

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. Melden Sie sich beim Frontend als Benutzer des Unternehmens an.
1. Überprüfen Sie die Seite der Frontend-Kategorie .

<u>Erwartete Ergebnisse</u>:

Die neu zugewiesenen Produkte werden an der Vorderseite angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die neu zugewiesenen Produkte werden nicht auf der Vorderseite angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
