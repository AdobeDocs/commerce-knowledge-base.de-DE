---
title: "MDVA-40134: GraphQL gibt verwandte Produkte nicht zurück, wenn der freigegebene Katalog aktiviert ist."
description: Der Patch MDVA-40134 behebt das Problem, dass GraphQL verwandte Produkte nicht zurückgibt, wenn der freigegebene Katalog aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-40134. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: 7b14355a-1c14-4c80-9426-6c40505d638b
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-40134: GraphQL gibt verwandte Produkte nicht zurück, wenn der freigegebene Katalog aktiviert ist

Der Patch MDVA-40134 behebt das Problem, dass GraphQL verwandte Produkte nicht zurückgibt, wenn der freigegebene Katalog aktiviert ist. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 ist installiert. Die Patch-ID lautet MDVA-40134. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

GraphQL gibt verwandte Produkte nicht zurück, wenn der freigegebene Katalog aktiviert ist.

<u>Voraussetzungen</u>:

B2B-Module müssen installiert sein.
Die Instanz darf nur mit den Beispieldaten sauber sein.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **Stores** > **Konfiguration** > **Allgemein** > **B2B-Funktionen** und aktivieren **Firmen- und freigegebener Katalog**.
1. Navigieren Sie zu **Katalog** > **Freigegebener Katalog** und fügen Sie alle Produkte zum **Allgemeiner Katalog**.
1. Verwenden Sie die Beispieldaten und ändern Sie das Joust Duffle Bag (SKU 24-MB01).
1. under **Verwandte Produkte**, fügen Sie die beiden Duffle-Taschen hinzu (ID 7 und 13).
1. Senden Sie eine **Post** Anfrage:

<pre>{ products(filter: {sku: {eq: "24-MB01"}}, sort: {name: ASC}) { items { related_products { uid name } } } } } }</pre>

<u>Erwartete Ergebnisse</u>:

Zugehörige Produkte werden in der GraphQL-Antwort angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Benutzer erhalten den folgenden Fehler:

<pre>Der Rückgabewert von Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor::getStoreId() muss vom Typ int, null return {"exception":"[object] (GraphQL\\Error\\Error(code: 0): Der Rückgabewert von Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor::getStoreId() muss vom Typ int, null zurückgegeben sein </pre>

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
