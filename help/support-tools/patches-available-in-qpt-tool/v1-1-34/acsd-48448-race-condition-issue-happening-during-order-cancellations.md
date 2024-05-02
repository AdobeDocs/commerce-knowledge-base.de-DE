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

# ACSD-48448: *[!UICONTROL Race]* Bedingungsfehler bei Auftragsabbrüchen, der zu einer doppelten Eingabe in `inventory_reservation` table

Der Patch ACSD-48448 behebt das Problem, bei dem der *[!UICONTROL Race]* -Bedingungsfehler tritt während der Absage einer Bestellung auf, was zu duplizierten Einträgen in der `inventory_reservation` Tabelle. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.34 ist installiert. Die Patch-ID lautet ACSD-48448. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2 und 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

*[!UICONTROL Race]* -Bedingungsfehler tritt während der Absage einer Bestellung auf, was zu duplizierten Einträgen in der `inventory_reservation` Tabelle.

<u>Zu reproduzierende Schritte</u>:

1. Bestellung aufgeben.
1. Überprüfen Sie die `inventory_reservation` -Tabelle, um sicherzustellen, dass ein Datensatz für die `order_placed` -Ereignis.
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

Duplizierte Datensätze werden im `inventory_reservation` Tabelle für `order_canceled`.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
