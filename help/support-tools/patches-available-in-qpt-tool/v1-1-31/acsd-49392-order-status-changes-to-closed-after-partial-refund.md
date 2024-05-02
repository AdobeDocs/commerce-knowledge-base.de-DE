---
title: "ACSD-49392: Auftragsstatus ändert sich nach teilweiser Rückerstattung zu schließen"
description: Wenden Sie den Patch ACSD-49392 an, um das Adobe Commerce-Problem zu beheben, bei dem der Auftragsstatus nach einer teilweisen Rückerstattung für ein gebündeltes Produkt zu "geschlossen"geändert wird.
exl-id: fca6f502-e224-4444-b0d0-f823853c9458
feature: Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-49392: Auftragsstatus wird nach teilweiser Rückerstattung geschlossen

Der Patch ACSD-49392 behebt das Problem, dass sich der Bestellstatus nach einer teilweisen Rückerstattung für ein gebündeltes Produkt in &quot;geschlossen&quot;ändert. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.31 installiert ist. Die Patch-ID lautet ACSD-49392. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.3.7-p4 und 2.4.1 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Änderung des Bestellstatus nach teilweiser Rückerstattung für ein gebündeltes Produkt.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Adobe Commerce an und erstellen Sie ein beliebiges gebündeltes Produkt oder verwenden Sie das vorhandene gebündelte Produkt.
1. Bestellen Sie mit diesem gebündelten Produkt eine Menge größer als 1.
1. Wechseln Sie zu &quot;admin&quot;und öffnen Sie die in Schritt 2 erstellte Bestellung von **[!UICONTROL Sales]** > **[!UICONTROL Order]** und eine Rechnung erstellen. Beobachten Sie den Bestellstatus. Es wird verarbeitet.
1. Erstellen Sie ein Teil-Credit Memo (keine Rückerstattung für alle Produkte im Bundle).
1. Überprüfen Sie den Bestellstatus.

<u>Erwartete Ergebnisse</u>

Nachdem Sie ein Teil-Kreditmemo für das gebündelte Produkt erstellt haben, wird der Auftragsstatus verarbeitet.

<u>Tatsächliche Ergebnisse</u>

Nach der Erstellung eines Teilgutschrift-Memos für das gebündelte Produkt ist der Auftragsstatus abgeschlossen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
