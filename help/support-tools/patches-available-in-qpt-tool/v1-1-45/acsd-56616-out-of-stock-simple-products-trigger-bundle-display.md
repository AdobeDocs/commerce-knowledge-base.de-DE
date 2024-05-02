---
title: "ACSD-56616: Storefront-Anzeige gebündelter Produkte bei einfacher Lagerhaltung"
description: Wenden Sie den Patch ACSD-56616 an, um das Adobe Commerce-Problem zu beheben, bei dem gebündelte Produkte unerwartet auf der Storefront angezeigt werden, wenn alle zugehörigen einfachen Produkte nicht vorrätig sind.
feature: Products
role: Admin, Developer
exl-id: 6cf8e15d-38a5-42b6-aee7-67410b501404
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-56616: Storefront-Anzeige von gebündelten Produkten während einfacher Lagerknappheit.

Der Patch ACSD-56616 behebt das Problem, dass gebündelte Produkte unerwartet auf der Storefront angezeigt werden, wenn alle verknüpften einfachen Produkte nicht vorrätig sind. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 ist installiert. Die Patch-ID ist ACSD-56616. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Falsche Anzeige von gebündelten Produkten in Storefront bei einfacher Lagerhaltung.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue Website/einen neuen Store/eine neue Storefront.
1. Erstellen Sie eine neue Quelle.
1. Erstellen Sie ein neues Lager und weisen Sie es der neu erstellten Website zu.
1. Konfigurieren Sie Indexer, um sie planmäßig zu aktualisieren.
1. Generieren Sie zwei einfache Produkte, S1 (qty = 1) und S2 (qty = 1), und weisen Sie sie dem neuen Lager und der neuen Website zu.
1. Erstellen *bundles1* Produkt und verknüpfen es mit einer neuen Website, indem es in eine Kategorie platziert wird *CAT*.
1. Definieren Sie zwei erforderliche Dropdown-Optionen und verknüpfen Sie ein einfaches Produkt *S1* zu Option1 und *S2* auf Option 2.
1. Speichern Sie die Produkte.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** und aktivieren *Hinzufügen von Store-Code zur URL* = *Ja*.
1. Öffnen Sie die Storefront und kaufen Sie das gebündelte Produkt.
1. Führen Sie zweimal cron aus.
1. Kehren Sie zu *CAT* Kategorie.

<u>Erwartete Ergebnisse</u>:

Die *bundle1* Das Produkt ist nicht vorrätig.

<u>Tatsächliche Ergebnisse</u>:

Die *bundle1* Produkt ist sichtbar mit Preis = *0$*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
