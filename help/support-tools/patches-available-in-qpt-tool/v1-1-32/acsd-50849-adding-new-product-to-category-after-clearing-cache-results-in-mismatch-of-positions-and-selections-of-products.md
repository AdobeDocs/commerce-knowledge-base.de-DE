---
title: "ACSD-50849: Das Hinzufügen eines neuen Produkts nach dem Löschen des Cache führt zu Inkongruenzen"
description: Wenden Sie den Patch ACSD-50849 an, um das Adobe Commerce-Problem zu beheben, bei dem das Hinzufügen eines neuen Produkts zur Kategorie nach dem Löschen des Caches zu einer Inkongruenz zwischen Positionen und Auswahl der vorhandenen Produkte führt.
feature: Cache, Categories, Products
role: Admin
exl-id: 3c797bf4-45da-4500-8c06-8c1007249738
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-50849: Das Hinzufügen eines neuen Produkts nach dem Löschen des Cache führt zu inkonformen Ergebnissen

Der Patch ACSD-50849 behebt das Problem, dass das Hinzufügen eines neuen Produkts zur Kategorie nach dem Löschen des Caches zu einer Inkongruenz zwischen Positionen und Auswahl der vorhandenen Produkte führt. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) QPT 1.1.32 ist installiert. Die Patch-ID ist ACSD-50849. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn Sie ein neues Produkt zur Kategorie hinzufügen, nachdem Sie den Cache geleert haben, stimmen die Positionen und Auswahlen der vorhandenen Produkte nicht überein.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie zwei Produkte.
1. Weisen Sie einer Kategorie ein Produkt zu.
1. Öffnen Sie die Kategorie über den Administrator.
1. Cache leeren `bin/magento cache:flush`.
1. Fügen Sie der Kategorie das zweite Produkt hinzu.

<u>Erwartete Ergebnisse</u>:

Die in der Kategorie zugewiesenen vorhandenen Produkte werden nicht automatisch entfernt.

<u>Tatsächliche Ergebnisse</u>:

Das erste (vorhandene) Produkt wird automatisch entfernt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
