---
title: 'ACSD-60441: Beim Aktualisieren von Kunden über den API-Endpunkt V1/Customers [!DNL REST] wird ein Fehler ausgegeben'
description: Wenden Sie den Patch ACSD-60441 an, um das Adobe Commerce-Problem zu beheben, bei dem bei der Aktualisierung von Kunden über die API V1/customer [!DNL REST] API bei der Verwendung des vom Backend generierten Integrationszugriffs-Tokens ein Fehler ausgegeben wird.
feature: REST, Customers
role: Admin, Developer
exl-id: fdc18060-5c6d-4f95-84d3-9ad120fe3a7d
source-git-commit: 06f751e43ef825c0eb29cb9b42eb41f07c308625
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-60441: Beim Aktualisieren von Kunden über den API-Endpunkt `V1/customers` [!DNL REST] wird ein Fehler ausgegeben

Der Patch ACSD-60441 behebt das Problem, dass das Aktualisieren von Kunden über die API `V1/customers` [!DNL REST] bei Verwendung des vom Backend generierten Integrationszugriffstokens einen Fehler verursacht. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 installiert ist. Die Patch-ID ist ACSD-60441. Bitte beachten Sie, dass dieses Problem in Adobe Commerce 2.4.8 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p8

**Kompatibel mit Adobe Commerce-Versionen**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p9, 2.4.5-p8, 2.4.6-p6, 2.4.7-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Aktualisieren von Kunden über den API-Endpunkt `V1/customers` [!DNL REST] bei Verwendung des vom Backend generierten Integrationszugriffstokens wird ein Fehler ausgegeben.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Integration über den Administrator.
1. Senden Sie mit dem Integrations-Token eine [!DNL POST] -Anfrage an `rest/default/V1/customers/<customer_id>`.

   ```json
   {
     "customer": {
       "email": "roni_cost@example.com",
       "firstname": "Veronica",
       "lastname": "Costello"
     }
   }
   ```

<u>Erwartete Ergebnisse</u>:

Die Kundendaten werden aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten den folgenden Fehler:

    &quot;json
    {
    &quot;message&quot;: &quot;Ein Kunde mit derselben E-Mail-Adresse ist bereits auf einer verknüpften Website vorhanden.&quot;,
    &quot;trace&quot;: ...
    
    &quot;

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
