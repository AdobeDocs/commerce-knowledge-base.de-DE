---
title: "ACSD-49389: Bereit für Abruf-E-Mail, die von der API gesendet wird, wenn sie nicht bereit für Abruf ist"
description: Wenden Sie den Patch ACSD-49389 an, um das Adobe Commerce-Problem zu beheben, bei dem eine für die Abruf-E-Mail bereite E-Mail von der API gesendet wird, wenn die Bestellung nicht bereit zur Abholung ist.
exl-id: a1baae06-cf36-448b-bda4-aff1e5ca68db
feature: REST, Communications
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49389: Bereit für die Abruf-E-Mail, die von der API gesendet wird, wenn sie nicht bereit zur Abruf ist

Der Patch ACSD-49389 behebt das Problem, dass eine Vorabruf-E-Mail von der API gesendet wird, wenn die Bestellung noch nicht abgeholt werden kann. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 ist installiert. Die Patch-ID lautet ACSD-49389. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [QPT-Landingpage](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eine Vorabruf-E-Mail wird von der API gesendet, wenn die Bestellung noch nicht abgeholt werden kann.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren *[!UICONTROL In-Store Delivery]* -Methode.
1. Erstellen Sie eine Stock-Quelle mit aktiviertem Pickup-Speicherort.
1. Erstellen Sie ein neues Lager mithilfe der Haupt-Website mit der oben erstellten Quelle.
1. Erstellen Sie ein Produkt, das dieselbe Quelle zuweist.
1. Legen Sie die Aktienanzahl = 1 fest.
1. Sehen Sie sich das in Schritt 4 erstellte Produkt an, indem Sie die *[!UICONTROL In-Store Delivery]* -Methode aus der Storefront.
1. Erstellen Sie eine Rechnung für die Bestellung.
1. Setzen Sie die Produktmenge auf *0* und machen es aus Lager.
1. Posten Sie die folgende API-Anfrage:

```
{
    "orderIds": [
        1
    ]
}
```

<u>Erwartete Ergebnisse</u>:

Bereit für die Abruf-E-Mail wird nicht gesendet.

<u>Tatsächliche Ergebnisse</u>:

API-Rückgaben *Die Bestellung kann nicht abgerufen werden*, aber die Abruf-E-Mail bereit wird gesendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
