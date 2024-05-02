---
title: 'MC-42528: GraphQL-Abfrage von categoryList zeigt alle Kategorien an'
description: Der Patch MC-42528 behebt das Problem, bei dem die GraphQL-Abfrage von "categoryList"sowohl zugewiesene als auch nicht zugewiesene Kategorien zurückgibt, wenn die Browsing-Kategorie einer bestimmten Kategorie auf "Ablehnen"gesetzt ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 installiert ist. Die Patch-ID ist MC-42528. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: 8bb29f43-92ae-4f37-b147-7121b55c185b
feature: Catalog Management, Categories, GraphQL, Customer Service
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MC-42528: GraphQL-Abfrage von categoryList zeigt alle Kategorien an

Der Patch MC-42528 löst das Problem, bei dem die GraphQL-Abfrage von `categoryList` gibt sowohl zugewiesene als auch nicht zugewiesene Kategorien zurück, wenn die Browsing-Kategorie einer bestimmten Kategorie auf &quot;Ablehnen&quot;gesetzt ist. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 ist installiert. Die Patch-ID ist MC-42528. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

GraphQL-Abfrage `categoryList` gibt sowohl zugewiesene als auch nicht zugewiesene Kategorien zurück.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie zwei Kategorien, CAT1 und CAT2, und weisen Sie jeder Kategorie wenige Produkte zu.
1. Erstellen Sie einen privaten freigegebenen Katalog.
1. Erstellen Sie einen Unternehmensbenutzer und weisen Sie ihn dem erstellten freigegebenen Katalog zu.
1. Weisen Sie dem benutzerdefinierten Katalog CAT1 zu und legen Sie die Kategorieberechtigung für die Kundengruppe des privaten Katalogs auf &quot;Browsing-Kategorie zulassen&quot;fest.
1. Legen Sie die Kategorieberechtigung für CAT2 für die Benutzergruppe des privaten Katalogs auf &quot;Browsing-Kategorie verweigern&quot;fest.
1. Führen Sie die `categoryList` oder `categories` GraphQL-Abfrage als Unternehmensbenutzer.

<u>Erwartete Ergebnisse</u>:

Nur die CAT1 wird in der Antwort angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Alle Kategorien werden in der Antwort angezeigt, unabhängig von den Browserberechtigungen der Kategorie.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) Abschnitt.
