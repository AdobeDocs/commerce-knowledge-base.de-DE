---
title: "ACSD-46683: Versandpreis zeigt *Noch nicht berechnet* an."
description: Wenden Sie den Patch ACSD-46683 an, um das Adobe Commerce-Problem zu beheben, bei dem der Versandpreis *Noch nicht berechnet* anzeigt.
exl-id: 77986612-87b7-4f50-afaf-1cfe9a4feb6f
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-46683: Versandpreis zeigt *Noch nicht berechnet*

Der Patch ACSD-46683 behebt das Problem, bei dem der Versandpreis angezeigt wird *Noch nicht berechnet*. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 installiert ist. Die Patch-ID ist ACSD-46683. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Versandpreis zeigt *Noch nicht berechnet*.

<u>Voraussetzungen</u>:

Adobe Commerce Inventory management (MSI)-Module sind installiert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein einfaches Produkt und setzen Sie seinen Preis auf *34 $*.
1. Konfigurieren Sie die Versandmethode für den kostenlosen Versand.
1. Konfigurieren Sie mindestens eine weitere Versandmethode.
1. Navigieren Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** und erstellen Sie eine neue Regel:
   * Name = *75 Mehr*
   * Coupon = Keine
   * Priorität = 1
   * Bedingungen: Die Zwischensumme ist gleich oder größer als *75 $*
   * Aktionen:
      * Auf Versandbetrag anwenden = Ja
      * Nachfolgende Regeln verwerfen = Nein
      * Kostenloser Versand = für Sendungen mit übereinstimmenden Artikeln
1. Erstellen Sie eine weitere Preisregel für den Warenkorb:
   * Name = *35off*
   * Priorität = 0
   * Coupon = spezifischer Coupon
   * Couponcode = 35off
   * Aktionen:
      * Anwenden = Prozentsatz des Produktpreisrabatts
      * Rabattbetrag = 35
      * Anwenden auf Versandbetrag = Nein
      * Nachfolgende Regeln verwerfen = Ja
      * Kostenloser Versand = Nein
1. Öffnen Sie die Storefront und fügen Sie dem Warenkorb drei Produkte hinzu, sodass die Zwischensumme 75 USD überschreitet.
1. Fahren Sie fort, um als Gast auszuchecken.
1. Wählen Sie im Versandschritt **0 USD - kostenloser Versand** und fahren Sie mit dem Zahlungsschritt fort.
1. Überprüfen Sie die [!UICONTROL Order Summary] im Zahlungsschritt. Er zeigt *[!UICONTROL $0 - Free Shipping - Free]*.
1. Anwenden des Gutscheincodes *35off*, wird die Zwischensumme aktualisiert und unter 75 USD gebracht.
1. Überprüfen [!UICONTROL Order Summary] im Zahlungsschritt.

<u>Erwartete Ergebnisse</u>:

Die folgende Meldung wird angezeigt: *Die ausgewählte Versandmethode ist nicht verfügbar. Bitte wählen Sie für diese Bestellung eine andere Versandmethode aus.*

<u>Tatsächliche Ergebnisse</u>:

Der Versandpreis wird angezeigt *Noch nicht berechnet*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
