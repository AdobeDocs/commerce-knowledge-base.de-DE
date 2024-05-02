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

Der Patch ACSD-51899 behebt das Problem, dass die standardmäßige Versandadresse automatisch mit einer falschen Adresse gefüllt wird. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-51899. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die standardmäßige Versandadresse enthält automatisch eine falsche Adresse

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren **In Store Pickup** nach der Versandmethode.
1. Erstellen *stock* und *source*.
1. Erstellen Sie das Produkt und weisen Sie es der Quelle zu.
1. Produkt zum Warenkorb hinzufügen.
1. Klicken Sie auf **Zur Kasse gehen** aus dem Mini-Warenkorb
1. Geben Sie die Test-E-Mail-Adresse ein und wählen Sie **Im Store auswählen**.
1. Klicken Sie auf **Store auswählen** und wählen Sie einen Speicherort aus, aus dem Sie auswählen möchten.
1. Klicken Sie auf **next** Schaltfläche.
1. Navigieren Sie zum **Startseite** durch Klick auf das Logo des Stores.
1. Öffnen Sie die **Mini-Warenkorb**.
1. Klicken Sie auf den unteren Hyperlink namens **Warenkorb anzeigen und bearbeiten**.
1. Klicks **Zur Kasse gehen**.
1. Klicken Sie auf die Versandschaltfläche in der Versandseite.

<u>Erwartete Ergebnisse</u>

Das Feld Lieferadresse bleibt leer, außer für *Land, Region und Postleitzahl*.

<u>Tatsächliche Ergebnisse</u>

Die standardmäßige Versandadresse wird automatisch mit *In-Store-Abruf* Adresse nach der Aktualisierung der Seite.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
