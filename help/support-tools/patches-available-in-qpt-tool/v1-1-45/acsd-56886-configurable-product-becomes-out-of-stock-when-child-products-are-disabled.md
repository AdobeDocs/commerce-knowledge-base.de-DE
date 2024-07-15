---
title: "ACSD-56886: Konfigurierbares Produkt wird nicht mehr vorrätig, wenn untergeordnete Produkte deaktiviert sind"
description: Wenden Sie den Patch ACSD-56886 an, um das Adobe Commerce-Problem zu beheben, bei dem das konfigurierbare Produkt nicht mehr vorrätig ist, wenn Produkte deaktiviert sind.
feature: Products
role: Admin, Developer
exl-id: 809b9829-283f-4e3c-bf27-1944057f944f
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-56886: Konfigurierbares Produkt wird nicht mehr vorrätig, wenn untergeordnete Produkte deaktiviert sind

Der Patch ACSD-56886 behebt das Problem, dass das konfigurierbare Produkt nicht mehr vorrätig ist, wenn untergeordnete Produkte deaktiviert sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 installiert ist. Die Patch-ID ist ACSD-56886. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das konfigurierbare Produkt wird nicht mehr vorrätig, wenn untergeordnete Produkte deaktiviert sind.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich als Administrator an.
1. Legen Sie alle Indexer im Modus **[!UICONTROL Update By Schedule]** fest.
1. Erstellen Sie das folgende konfigurierbare Produkt:

   * Name = *TEST KONFIGURABLE 1*
   * Attribut = *Farbe*
   * Werte = *red* und *black*
   * Preis des untergeordneten **red** -Produkts = *$100*;
   * Preis des untergeordneten &quot;schwarzen&quot;Produkts = *$200*.

1. Erstellen Sie das folgende geplante Update für das konfigurierbare Produkt:

   * Startdatum = *3* Minuten ab jetzt.
   * Enddatum = *5* Minuten nach Startdatum.
   * Produktname = *TEST CONFIGURABLE 1, bearbeitet*.
   * Deaktivieren Sie das untergeordnete Produkt **red** im Abschnitt **Konfigurierbar** .

1. Warten Sie auf das Startdatum.
1. Öffnen Sie die konfigurierbaren Produktdetails in der Storefront.

<u>Erwartete Ergebnisse</u>:

Das konfigurierbare Produkt wird als **In Stock** mit der Beschriftung **So niedrig wie 200** angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Das konfigurierbare Produkt wird als **Nicht auf Lager** angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
