---
title: 'ACSD-47937: aufgrund von Caching auf Anwendungsebene nicht gesendete Preisabsturzbenachrichtigungen'
description: Wenden Sie den Patch ACSD-47937 an, um das Adobe Commerce-Problem zu beheben, bei dem aufgrund der Zwischenspeicherung auf Anwendungsebene nicht immer Preisabbruchbenachrichtigungen gesendet werden.
exl-id: f39c9ef6-4689-427f-bd61-3a52dec88be2
feature: Admin Workspace, Cache, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-47937: aufgrund von Caching auf Anwendungsebene nicht gesendete Preisabsturzbenachrichtigungen

Der Patch ACSD-47937 behebt das Problem, dass aufgrund der Zwischenspeicherung auf Anwendungsebene nicht immer Preisabbruchbenachrichtigungen gesendet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 installiert ist. Die Patch-ID ist ACSD-47937. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 und 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4, 2.4.5 und 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Kunden erhalten keine E-Mail zum Produktpreisverfall für nachfolgende Produktpreisänderungen.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie **[!UICONTROL Product Alert]** sowohl für *[!UICONTROL Price Changes]* als auch für *[!UICONTROL Back in Stock]* in **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]**.
1. Aktivieren Sie **[!UICONTROL Display Out of Stock Products]**.
1. Erstellen Sie ein einfaches Produkt (ABC) mit qty = 0.
1. Erstellen Sie einen Kunden aus der Storefront und abonnieren Sie das obige Produkt, um Produktwarnungen für Preisrückgänge zu erhalten.
1. Starten Sie die Produktwarnung für Kunden.

   ```PHP
   bin/magento queue:consumers:start product_alert
   ```

1. Legen Sie den Preis für das ABC-Produkt ab.
1. Trigger des Produkt-Warnhinweis-Crons.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Legen Sie den Preis für das ABC-Produkt erneut ab.
1. Trigger des Produkt-Warnhinweis-Crons.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

>[!NOTE]
>
>Wenn Sie nicht mit dem [!DNL n98]-Tool vertraut sind, können Sie `bin/magento cron:run command` wie gewohnt ausführen und die `cron_schedule`-Tabelle überwachen, um sicherzustellen, dass `catalog_product_alert` Auftrag den Erfolgsstatus erhält.

<u>Erwartete Ergebnisse</u>:

Die zweite Preissenkungs-E-Mail wird gesendet.

<u>Tatsächliche Ergebnisse</u>:

Die zweite Preissenkungs-E-Mail wird nicht gesendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
