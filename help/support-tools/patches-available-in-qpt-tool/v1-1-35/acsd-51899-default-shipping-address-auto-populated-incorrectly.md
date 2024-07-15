---
title: "ACSD-51899: Standard-Versandadresse falsch ausgefüllt"
description: Wenden Sie den Patch ACSD-51899 an, um das Adobe Commerce-Problem zu beheben, bei dem die standardmäßige Versandadresse automatisch mit einer falschen Adresse gefüllt wird.
feature: Checkout
role: Admin
exl-id: 67100fcd-e98f-4740-8f1f-fcc820f4c75d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-51899: Standardmäßige Versandadresse falsch ausgefüllt

Der Patch ACSD-51899 behebt das Problem, dass die standardmäßige Versandadresse automatisch mit einer falschen Adresse gefüllt wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-51899. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die standardmäßige Versandadresse enthält automatisch eine falsche Adresse

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie **In Store Pickup** unter Versandmethode.
1. Erstellen Sie *stock* und *source*.
1. Erstellen Sie das Produkt und weisen Sie es der Quelle zu.
1. Produkt zum Warenkorb hinzufügen.
1. Klicken Sie im Mini-Warenkorb auf **Weiter zum Checkout**.
1. Geben Sie die Test-E-Mail-Adresse ein und wählen Sie **Im Store wählen** aus.
1. Klicken Sie auf die Schaltfläche **Store auswählen** und wählen Sie einen Speicherort aus, aus dem Sie auswählen möchten.
1. Klicken Sie auf die Schaltfläche &quot;**next**&quot;.
1. Navigieren Sie zur **Homepage**, indem Sie auf das Store-Logo klicken.
1. Öffnen Sie den **Mini-Warenkorb**.
1. Klicken Sie auf den unteren Hyperlink mit dem Namen **Warenkorb anzeigen und bearbeiten**.
1. Klicken Sie auf **Fahren Sie mit dem Checkout fort**.
1. Klicken Sie auf die Versandschaltfläche in der Versandseite.

<u>Erwartete Ergebnisse</u>

Das Feld für die Lieferadresse bleibt leer, mit Ausnahme von *Land, Region und Postleitzahl*.

<u>Tatsächliche Ergebnisse</u>

Die standardmäßige Versandadresse wird nach dem Aktualisieren der Seite automatisch mit der Adresse *In-Store-Abruf* gefüllt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
