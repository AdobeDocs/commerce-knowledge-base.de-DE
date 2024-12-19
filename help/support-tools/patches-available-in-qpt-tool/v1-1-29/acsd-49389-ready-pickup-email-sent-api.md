---
title: 'ACSD-49389: Abholbereitschafts-E-Mail, die von der API gesendet wird, wenn sie nicht abholbereit ist'
description: Adobe Commerce Wenden Sie den Patch von ACSD-49389 an, um das Problem zu beheben, dass die API eine E-Mail zur Abholung sendet, wenn die Bestellung nicht zur Abholung bereit ist.
exl-id: a1baae06-cf36-448b-bda4-aff1e5ca68db
feature: REST, Communications
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49389: Abholbereitschafts-E-Mail, die von der API gesendet wird, wenn sie nicht abholbereit ist

Der Patch von ACSD-49389 behebt das Problem, dass eine abholbereite E-Mail von der API gesendet wird, wenn die Bestellung nicht abholbereit ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 installiert ist. Die Patch-ID ist ACSD-49389. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches`-Paket auf die neueste Version und überprüfen Sie die Kompatibilität auf der [QPT-Landingpage](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Eine abholbereite E-Mail wird von der API gesendet, wenn die Bestellung nicht abholbereit ist.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie *[!UICONTROL In-Store Delivery]* Methode.
1. Erstellen Sie eine Lagerquelle mit aktiviertem Abholort.
1. Erstellen Sie einen neuen Bestand auf der Haupt-Website mit der oben erstellten Quelle.
1. Erstellen Sie ein Produkt, das dieselbe Quelle zuweist.
1. Lagermenge = 1 festlegen.
1. Sehen Sie sich das in Schritt 4 erstellte Produkt mit der *[!UICONTROL In-Store Delivery]* -Methode aus der Storefront an.
1. Rechnung für die Bestellung erstellen.
1. Stellen Sie die Menge des Produkts auf *0* ein und machen Sie es ausverkauft.
1. Posten Sie die folgende API-Anfrage:

```
{
    "orderIds": [
        1
    ]
}
```

<u>Erwartete Ergebnisse</u>:

Abholbereitschafts-E-Mail wird nicht gesendet.

<u>Tatsächliche Ergebnisse</u>:

Die API gibt *Bestellung ist nicht abholbereit* aber die Abholbereitschafts-E-Mail wird gesendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
