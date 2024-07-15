---
title: "ACSD-48448: Problem mit der Wettlaufsituation bei Auftragsabbrüchen, die zu dupliziertem Eintrag in der Tabelle inventory_reservation führen"
description: Wenden Sie den Patch ACSD-48448 an, um das Leistungsproblem von Adobe Commerce zu beheben, bei dem das Problem mit der Race-Bedingung während der Auftragsabbrüche auftritt, was zu duplizierten Einträgen in der Tabelle inventory_reservation führt.
feature: Orders, Checkout
role: Admin
exl-id: 69d00219-bc9f-4531-9e85-38476c2258ed
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-48448: *[!UICONTROL Race]* Bedingungsfehler bei Auftragsabbrüchen, der zu einem doppelten Eintrag in der Tabelle `inventory_reservation` führte

Der Patch ACSD-48448 behebt das Problem, dass das Problem mit der *[!UICONTROL Race]*-Bedingung während der Auftragsabbrüche auftritt, was zu duplizierten Einträgen in der `inventory_reservation`-Tabelle führt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.34 installiert ist. Die Patch-ID lautet ACSD-48448. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2 und 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Problem mit der *[!UICONTROL Race]* -Bedingung tritt während der Stornierung einer Bestellung auf, was zu duplizierten Einträgen in der `inventory_reservation` -Tabelle führt.

<u>Zu reproduzierende Schritte</u>:

1. Bestellung aufgeben.
1. Überprüfen Sie die Tabelle `inventory_reservation` , um sicherzustellen, dass ein Datensatz für das Ereignis `order_placed` vorhanden ist.
1. Führen Sie das angehängte Skript aus, um die Bestellung parallel abzubrechen (denken Sie daran, URL und orderID zu ändern).

`bash cancel_order.sh`

```
#!/bin/bash
baseUrl=" "
orderId=3
token=$(curl --location --request POST "${baseUrl}rest/V1/integration/admin/token" \
 -H 'Content-Type: application/json' \
 -d '{
  "username": "admin",
  "password": "password"
}')
echo ${token//\"/}
curl --location --request POST "${baseUrl}/rest/V1/orders/${orderId}/cancel" \
 -H "Authorization:Bearer ${token//\"/}" \
 -H 'Content-Type: application/json' \
 &
sleep 0.1;
curl --location --request POST "${baseUrl}/rest/V1/orders/${orderId}/cancel" \
 -H "Authorization:Bearer ${token//\"/}" \
 -H 'Content-Type: application/json' \
wait
```

<u>Erwartete Ergebnisse</u>:

Datensätze werden nicht dupliziert.

<u>Tatsächliche Ergebnisse</u>:

Duplizierte Datensätze werden in der Tabelle `inventory_reservation` für `order_canceled` erstellt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
