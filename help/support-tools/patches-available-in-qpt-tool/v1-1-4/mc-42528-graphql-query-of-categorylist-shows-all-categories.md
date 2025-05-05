---
title: 'MC-42528: GraphQL-Abfrage der categoryList zeigt alle Kategorien an'
description: Der Patch MC-42528 löst das Problem, dass die GraphQL-Abfrage von „categoryList“ sowohl zugewiesene als auch nicht zugewiesene Kategorien zurückgibt, wenn die Navigationskategorie einer bestimmten Kategorie auf „Ablehnen“ eingestellt ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 installiert ist. Die Patch-ID lautet MC-42528. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
exl-id: 8bb29f43-92ae-4f37-b147-7121b55c185b
feature: Catalog Management, Categories, GraphQL, Customer Service
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MC-42528: GraphQL-Abfrage der categoryList zeigt alle Kategorien an

Der Patch MC-42528 löst das Problem, dass die GraphQL-Abfrage von `categoryList` sowohl zugewiesene als auch nicht zugewiesene Kategorien zurückgibt, wenn die Navigationskategorie einer bestimmten Kategorie auf „Ablehnen“ eingestellt ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 installiert ist. Die Patch-ID lautet MC-42528. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

GraphQL-Abfrage von `categoryList` gibt sowohl zugewiesene als auch nicht zugewiesene Kategorien zurück.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei Kategorien, CAT1 und CAT2, und weisen Sie jeder Kategorie wenige Produkte zu.
1. Erstellen Sie einen privaten freigegebenen Katalog.
1. Erstellen Sie einen Unternehmensbenutzer und weisen Sie ihn dem erstellten freigegebenen Katalog zu.
1. Weisen Sie CAT 1 dem benutzerdefinierten Katalog zu und legen Sie die Kategorieberechtigung für die Kundengruppe des privaten Katalogs auf die Kategorie „Durchsuchen zulassen“ fest.
1. Legen Sie die Kategorieberechtigung für CAT2 für die Kundengruppe des privaten Katalogs auf die Browsing-Kategorie „Ablehnen“ fest.
1. Führen Sie die `categoryList`- oder `categories` GraphQL-Abfrage als Firmenbenutzer aus.

<u>Erwartete Ergebnisse</u>:

In der Antwort wird nur CAT1 angezeigt.

<u>Tatsächliche Ergebnisse</u>:

In der Antwort werden alle Kategorien angezeigt, unabhängig von den Browserberechtigungen der Kategorie.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
