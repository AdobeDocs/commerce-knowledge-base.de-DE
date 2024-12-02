---
title: 'ACSD-57588: Fehler bei der Verarbeitung der Regions-ID beim Versand an mehrere Adressen'
description: Wenden Sie den Patch ACSD-57588 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Versand einer Bestellung an mehrere Adressen-Trigger bei der Verarbeitung der Regions-ID ein Fehler auftritt.
feature: Orders, Shipping/Delivery
role: Admin, Developer
exl-id: 01a33db3-fdbe-4acd-a617-45fb3aee6f3d
source-git-commit: 9bb839292a120a3dab5151d493f915619dbf5c06
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-57588: Fehler bei der Verarbeitung der Regions-ID beim Versand an mehrere Adressen

Der Patch ACSD-57588 behebt das Problem, dass beim Versand einer Bestellung an mehrere Adressen-Trigger bei der Verarbeitung der Regions-ID ein Fehler auftritt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 installiert ist. Die Patch-ID ist ACSD-57588. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Fehler bei der Verarbeitung der Regions-ID beim Versand an mehrere Adressen.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie die Zahlungsmethode [!DNL Braintree] .
1. Melden Sie sich als Kunde an der Storefront an.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und fahren Sie mit dem Anzeigen und Bearbeiten des Warenkorbs fort.
1. Fügen Sie mehrere Adressen *(z. B. UK, US, CA)* während des Checkout-Prozesses hinzu und überprüfen Sie die Bestellung.
1. Wählen Sie auf der Checkout-Seite die Kreditkartenzahlungsoption aus, geben Sie die erforderlichen Anmeldedaten ein und platzieren Sie die Bestellung.

<u>Erwartete Ergebnisse</u>:

Die Bestellung kann erfolgreich platziert werden.

<u>Tatsächliche Ergebnisse</u>:

Die Bestellung wird nicht platziert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
