---
title: '"ACSD-52202: Die standardmäßige Lagerverkaufsmenge ändert sich zu "0"mit Fehler, wenn der nicht standardmäßige Lagerbestand auf 0 qty in der Reihenfolge festgelegt ist."'
description: Wenden Sie den Patch ACSD-52202 an, um das Adobe Commerce-Problem zu beheben, bei dem eine standardmäßige Lagerverkaufsmenge fehlerhaft auf 0 geändert wird, wenn der nicht standardmäßige Lagerbestand in einer Bestellung auf 0 Menge eingestellt ist.
feature: Inventory, Products
role: Admin
exl-id: 8a3b5da4-cf16-41c8-b2d5-b740d638c745
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-52202: Die standardmäßige Lagerverkaufsmenge ändert sich zu 0, wenn der nicht standardmäßige Lagerbestand in einer Bestellung auf 0 Menge eingestellt ist.

Der Patch ACSD-52202 behebt das Problem, dass eine standardmäßige Lagerverkaufsmenge (qty) zu 0 fehlerhaft wird, wenn ein nicht standardmäßiges Lager in einer Bestellung auf 0 Menge eingestellt ist. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-52202. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die standardmäßige Lagerverkaufsmenge ändert sich zu 0, wenn der nicht standardmäßige Bestand in einer Bestellung auf 0 Menge eingestellt ist.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei [!DNL Admin].
1. Erstellen **website2**.
1. Benutzerdefiniert erstellen **source2**.
1. Benutzerdefiniert erstellen **stock2**.
1. Zuweisen der **source2** und **stock2** nach **website1** sowie die Standardquelle und den Standardbestand auf der Standardwebsite.
1. Einfaches Produkt erstellen und zuweisen **qty** = *10* für die Standardquelle und **qty** = *1* für die **source2** -Quelle.
1. Platzieren einer Bestellung mit **qty** = *1* für **website2**.
1. Erstellen Sie eine Rechnung und eine Sendung.
1. Überprüfen des einfachen Produkts **verkaufte Menge**.

<u>Erwartete Ergebnisse</u>:

Die **verkaufte Menge** = *10* für **source2**.

<u>Tatsächliche Ergebnisse</u>:

Die **verkaufte Menge** = *0* für beide Quellen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
